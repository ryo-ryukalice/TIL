turbolinks が生きている環境で `ReactDOM.render()` を `DOMContentLoaded` イベントで行うと 

```tsx
document.addEventListener('DOMContentLoaded', () => {
  ReactDOM.render(
    <App />,
    document.body
  )
});
```

`a` 要素のリンクを踏んでも発火しないので

```tsx
export const Footer = () => (
  <a href="/">タイトルへ戻る</a>
)
```

`turbolinks:load` を使う。

```diff
- document.addEventListener('DOMContentLoaded', () => {
+ document.addEventListener('turbolinks:load', () => {
    ReactDOM.render(
      <App />,
      document.body
    )
  });
```
