# Power Pattern
## Memorized with memo
> Stores the output of a function based on its input so if the function is called with the sam inputs, it returns cached result rather than recomputing the output.
> 
> Memorization relies on function purity, particular useful when dealing with expensive calculations.
## If we memoize every component, our app might be faster overall?
> No, memoized components that still re-render, its perform shallow comparison of the props to determine whether they have changed or not.
> 
> The problem is while scalar(primitive) can be compared quite accurately, non-scalar(reference type) cannot.
> 

#### Scalar
> They are immutable by nature, once a scalar value is set, it cannot be altered without creating a completely new value.
> 
> When comparing we're often interested in their actual content or value.
> 

#### Non-scalar
> They don't store data but rather a reference or pointer to where the data is stored in memory, function is also a non-scalar type.
> Multiple references can point to same memory location.
> 
> When comparing, non-scalar type are compared by their memory reference, not their by content.
> 

### Implementation
##### 1. Initial check
> Determines if this is the initial render of the component. if current is `null -> ` the component is being mounted for the first time.
##### 2. Type and fast path optimization.
> If these conditions are met, it sets the work-in-progress Fiber's tag to `SimpleComponent` indicating a simpler component type that can be updated more efficiently.
##### 3. DEV mode check
> In Dev mode `__DEV__` performs additional checks, like validating prop types and waring about deprecated features.
##### 4. Creating a new Fiber.
> If it is the initial render, a new Fiber is created, it sets up references and returns the child (new Fiber)
##### 5. Updating existing Fiber.
> If component is updating (`current !== null`), it performs similar dev mode checks. It then checks if the component needs an update by comparing the old props with new props using a shallow comparison.
##### 6. Bailing out of update.
> If the props are equal and ref hasn't changed, no further rendering work is needed for this component.
##### 7. Update work-in-progress Fiber
> If an update is needed, create a new work-in-progress child Fiber based on the current child with new props.

## Memoization with useMemo
> React.memo and useMemo are both tools for memoization but different purposes.
> 
> `React.memo` keep component from re-rendering. `useMemo` avoid expensive recalculations and preserve a consistent reference for the result.

### Built-in component (`div, button, input`) in react
#### Direct pass-through
> When pass a function prop to a built-in, React passed it through directly actual DOM. It does not create any wrappers or perform any additional work.
> 
> However, React use event delegation for handling events. `<button onClick={function}/>`.
> React did not attach the onClick handler directly to DOM button. Instead, React listens for all events at the top level using single event listener.
> This is attached to the root of the document, and relies on event bubbling to catch events that originate from individual elements
> 
> 

