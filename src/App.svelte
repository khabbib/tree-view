<script>
  import TreeViewNodes from './TreeViewNodes.svelte';

  let treeData = {
    label: 'Root',
    children: [
      {
        id: "rootId",
        label: 'Node 1',
        children: []
      }
    ]
  };

  function addNode(parentNode, newNode) {
    treeData = updateNode(treeData, parentNode.id, (node) => {
      return { ...node, children: [...node.children, newNode] };
    });
  }

  function updateNode(node, targetId, updateFn) {
    if (node.id === targetId) {
      return updateFn(node);
    }

    if (node.children && node.children.length > 0) {
      return { ...node, children: node.children.map(child => updateNode(child, targetId, updateFn)) };
    }

    return node;
  }
</script>

<div id="tree-ul">
  <TreeViewNodes treeData={treeData} nodes={treeData.children} {addNode} />
</div>
