# DOM
> HTML document modeled as a JavaScript object, DOM is the browser runtime's model of the document.

## Virtual DOM
> lightweight copy of DOM, with the key difference while real DOM is made up of Node Objects
> The VDOM is made up of **plain JS objects** that act as descriptions.
> 
> Allows web devs to create UI in a more efficient and performant way.
> In React, whenever whe changed UI the Virtual DOM is updated first, and then the real DOM is updated to match the changes in VDOM.
> 
> **Reconciliation**

## The Real DOM
HTML page is loaded into a web browser, it is parsed and converted into a tree of nodes and objects -**_Object Model_**-. The DOM is a live representation of the web page.

### Pitfalls
#### Performance
+ adding/removing an element or changing text/attributes. The browser has to recalculate the layout and repaint the affected parts of the page.

#### Cross-browser compatibility
+ Diff browser diff model documents, lead to inconsistencies 
+ Certain DOM elements and attributes may not be supported by all browsers 

##### Unified interface
> In raw Javascript, handling browser events can be tricky, accessing event properties might differ across browser.
> Some might use `event.target`, other `event.srcElement`. 
> 
> `SyntheticEvent`
> + Abstracts, proving a consistent way to interact with events.
> + `// Without React, browser-specific properties`
> + `const targetElement = event.target || event.srcElement`
> + `// In react, thanks to SyntheticEvent, it's consistent`
> + `function handlerClick(event) = event.target...`

##### Event delegation
##### Cross-functional enhancements

### Document Fragments
> Lightweight container that holds DOM nodes. Temporary staging area can make multiple changes without affecting the main DOM. 
> 
> Once you're done, you can append the `document fragment` to the DOM, triggering a single reflow and repaint.
> 
> Very close to React's virtual DOM
> 
##### Batches updates
> Instead of making multiple individual updates to the live DOM, batch all changes in a `document fragment ->` only one reflow and repaint occurs.

##### Memory efficiency
> When nodes are added to a document fragment, removed from their current parent in the DOM.
> 

##### No redundant rendering
> Document fragment is not part of the active document tree, changes to it don't affect the live document

## How the Virtual DOM Works
> Helps to mitigate the pifalls of the real DOM. Changes can be made to the virtual representation without directly modifying the real DOM.
> 
> React to use the virtual DOM to build user interface