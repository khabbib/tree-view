<script>
    import TreeViewNodes from "./TreeViewNodes.svelte";
    import {v4} from "uuid";
    
    export let node;
    export let treeData;
    export let addNode;
  
    let currentNode = node;
  
    function handleAddNode() {
      const id = v4();
      const newNode = {
        id,
        label: `Node ${id}`,
        children: [],
      };
      
      addNode(currentNode, newNode);
    }

</script>
  
 <ul>
    <div class="input-group">
      <div>
        {currentNode.label}
        <div>
          <button on:click={handleAddNode}>Add node</button>
        </div>
      </div>
    </div>
    {#if currentNode.children.length > 0}
      <TreeViewNodes {treeData} nodes={currentNode.children} {addNode} />
    {/if}
</ul>
