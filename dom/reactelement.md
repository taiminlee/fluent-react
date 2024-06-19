# React Element
> UI are represented as a tree of React Element. 
> 

# VDOM Versus DOM
> `React.createElement` creates React element `-> Virtual Element in memory` and `document.createElement` create DOM nodes
> 
> When a React component is rendered: 
> + `created` a new virtual DOM
> + `compares` it to previous VDOM tree.
> + `Calculates` the minimum of changes need to update
> + `Reconciliation` process.

## Efficient Updates
+ Recursive comparison.
+ If nodes at `root` level of the `two trees are different`, React will `replace` the `entire tree` with the new one.
+ If nodes at `root` level are `the same`, React will `update` the attributes of `the node` if they have changed
+ If the children of a node `different`, React will `update only the children` that have changed.
+ If the children of a node `are the same`, but their order changed, React will `reorder` the nodes in the real DOM without `re-creating` them.
+ If a node `removed` from the tree, React will `remove` it from the DOM.
+ If a node's type has `changed`, React will `remove` the old node and `create` a new node of the new type.
+ If the node has a `key prop`, React uses it to know if it should replace the node or not. Useful when reset the state of the components

## Unnecessary rerender
When component change states: 
+ Re-render component and all of its descendants
+ Does not skip components whose props have not changed
+ Cause of React didn't know which component depends on state of the component that changed
+ It has to re-render all of them to ensure that UI stays consistent.

