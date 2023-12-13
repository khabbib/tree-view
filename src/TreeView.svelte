<script>
  import TreeViewNode from "./TreeViewNode.svelte";
  import TreeViewNodes from "./TreeViewNodes.svelte";
  export let node;
  export let treeData;
  export let addNode;

  let currentNode = node;

</script>

<ul>
  <li>
    <TreeViewNode {node} {treeData} {addNode} />
    {#if currentNode.children.length > 0}
      <TreeViewNodes {treeData} nodes={currentNode.children} {addNode} />
    {/if}
  </li>
</ul>

