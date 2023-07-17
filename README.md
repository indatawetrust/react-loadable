- [中文](https://github.com/cx690/react-loadable/blob/main/README_zh_CN.md "中文")

A higher order component for loading components with dynamic imports. Support vite and webpack.

## Install

```
yarn add @cond/react-loadable
```
```sh
npm install @cond/react-loadable
```

## Usage

```javascript
import Loadable from '@cond/react-loadable';
import Loading from './my-loading-component';

const LoadableComponent = Loadable({
  loader: () => import('./my-component1'),
  loading: Loading,
  timeout: 20000,
});
```

```javascript
const LoadableComponent = Loadable(() => import('./my-component1'));
 
export default class App extends React.Component {
  render() {
    return <LoadableComponent/>;
  }
}

```

## Customizing rendering

```javascript
export const LoadableComponent = Loadable({
  loader: () => import('./my-component1'),
  loading: Loading,
  render(loaded, props) {
    const Component = loaded;
    const ref = props.forwardRef || undefined;

    return <Component {...props} ref={ref} />;
  },
});
```
