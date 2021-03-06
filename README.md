# preact-global

Auto-refreshing global component state for preact

See a demo [here](http://konsumer.js.org/preact-global/).

This uses context to give you a top-level state that can be refreshed. Install in your project with `npm i preact-global`. This makes it a sort of no-dependency, very small, very light, and very easy redux-replacement. See [example/](https://github.com/konsumer/preact-global/tree/master/example) for an example of usage.

Basic idea is this:

```js
import import { GlobalProvider, withGlobal } from 'preact-global'

// wrap all your components that use global-state:
const Demo = withGlobal((props, { setGlobal, whatever }) => (
  <div>
    <div>{whatever}</div>
    <button onClick={e => setGlobal('whatever', 'cool!')}>COOL IT</button>
  </div>
))

// setup the global provider in your app, somewhere at the top
const App = () => (
  <GlobalProvider whatever='intial value'>
    <Demo />
  </GlobalProvider>
)

```

Anywhere inside `GlobalProvider` you can get to the context, even many components deep. You can add any props you like to `GlobalProvider`, and they will get inserted into the context.
