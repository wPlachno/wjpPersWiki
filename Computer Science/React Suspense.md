Released in React 16.6, React Suspense is a feature designed to provide better loading indications for a better user experience. 
## Suspense Component
The most straightforward usage is the Suspense Component. A Suspense component is a wrapper over the component that loads, designed to allow for an alternate component to display when loading.
``` React
<Suspense fallback={<WidgetFallback />}>
	<WidgetComponent />
</Suspense>
```
In this example, the *WidgetFallback* component will display until the *WidgetComponent* loads.

## .lazy()
Components can be written to be imported in chunks using the lazy() method. This enhances speed by loading only what is necessary immediately, improves the user experience by notifying the user that something is being loaded, and allows for heavy components to be deferred until other components have loaded, decreasing the loading time of the page. With Suspense imported, the developer can dynamically import it.
``` React
import { Suspense } from 'react';
...
const WidgetComponent = lazy(() => import('./WidgetComponent'));
...
function App() {
  return (
    <div>
      <Suspense fallback={<div>Loading...</div>}>
        <WidgetComponent />
      </Suspense>
    </div>
  );
}
```

## How Suspense Works
When using React Suspense with asynchronous operations, it follows these steps:
1. After React loads, a component tree is rendered.
2. React looks to see whether any of its child components are in a suspended state when it comes across a Suspense component.
3. React will display the given fallback UI until the data is ready, if a child component is awaiting data (for example, as a result of a `lazy()` import or a data fetch).
4. React smoothly transitions to rendering the real content once the data is available.

Because this procedure is automated, handling asynchronous actions without coding sophisticated logic is significantly easier for developers.
\- freecodecamp.org/news/react-suspense/

[The above quoted URL](https://www.freecodecamp.org/news/react-suspense/) has a great tutorial on implementing a full data-fetching React Suspense component. 