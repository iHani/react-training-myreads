## Antes de tudo

### Intale o node
### Intale o postman

## Passo #1

### `npx create-react-app myreads`
O proprio facebook tem um boilerplate de React, <br>
pra não precisar fazer varias configurações na mão..
[create-react-app](https://github.com/facebook/create-react-app)

## Passo #2

Copiar o arquivo BooksAPI <br>
```

const api = process.env.REACT_APP_ENDPOINT


// Generate a unique token for storing your bookshelf data on the backend server.
let token = localStorage.token
if (!token)
  token = localStorage.token = process.env.REACT_APP_TOKEN || Math.random().toString(36).substr(-8)

const headers = {
  'Accept': 'application/json',
  'Authorization': token
}

export const get = (bookId) =>
  fetch(`${api}/books/${bookId}`, { headers })
    .then(res => res.json())
    .then(data => data.book)

export const getAll = () =>
  fetch(`${api}/books`, { headers })
    .then(res => res.json())
    .then(data => data.books)

export const update = (book, shelf) =>
  fetch(`${api}/books/${book.id}`, {
    method: 'PUT',
    headers: {
      ...headers,
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({ shelf })
  }).then(res => res.json())

export const search = (query) =>
  fetch(`${api}/search`, {
    method: 'POST',
    headers: {
      ...headers,
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({ query })
  }).then(res => res.json())
    .then(data => data.books)

```
Configurar .env <br>
```
REACT_APP_ENDPOINT=https://reactnd-books-api.udacity.com
REACT_APP_TOKEN={coloque uma chave unica}
```

