```tsx
  fetch('/api/games/', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      'X-CSRF-Token': document.querySelector('meta[name="csrf-token"]').getAttribute('content'),
    },
  }).then(data => console.log(JSON.stringify(data)))
    .catch(error => console.error(error));
```
