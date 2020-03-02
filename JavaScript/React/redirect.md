```typescript
const AuthLineCallback = () => (
  <>
  </>
)

AuthLineCallback.getInitialProps = ({res}: { res: any }) => {
  if (res) {
    res.writeHead(301, {
      Location: '/'
    });
    res.end();
  }

  return {};
};

export default AuthLineCallback
```
