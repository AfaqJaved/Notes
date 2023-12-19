```javascript
const express = require('express')
const app = express()

// respond with "hello world" when a GET request is made to the homepage
app.get('/todo', (req, res) => {
  res.send('hello world')
})

app.post('/todo', (req, res) => {
  res.send('add Todo')
})

app.put('/todo', (req, res) => {
  res.send('add Todo')
})

app.delete('/todo', (req, res) => {
  res.send('add Todo')
})
```