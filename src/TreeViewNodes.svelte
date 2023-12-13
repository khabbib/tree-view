<script>
  import TreeViewNodes from './TreeViewNodes.svelte';
  import TreeViewNode from './TreeViewNode.svelte';
  export let treeData;
  export let nodes;
  export let addNode;


</script>

<ul>
  {#each nodes as currentNode (currentNode.label)}
    <li>
      <TreeViewNode node={currentNode} {treeData} {addNode} />
      {#if currentNode.children.length > 0}
        <TreeViewNodes treeData={treeData} nodes={currentNode.children} {addNode} />
      {/if}
    </li>
  {/each}
</ul>
