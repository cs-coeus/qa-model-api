# Question Answering Model

This is an API service for `ModelQA` of `coeus`

## API Documentation
### `GET /heathcheck`
Request: `None`

Response: `'OK'` with HTTP Status `200`

### `POST /predict`
Request:
`"data"` is an array with three elements.
- The first element is a context article.
- The second element is keyword to ask with as an array with first element is actual keyword.
- The third element is an array of question templates.
```json
{
  "data": [
    "Lorem ipsum dolor sit amet, consectetur adipiscing elit.", 
    ["ipsum"],
    ["What is ", "Where is "]
  ]
}
```
Response:
`"result"` is an array of an array of question answer pair.
```json
{
  "result": [
    ["question 1", "answer 1"],
    ["question 2", "answer 2"]
  ]
}
```

## Run
1. Copy file `.env.example` into `.env` and fill in all necessary values
2. Make sure you have Docker installed on your system and running
3. Build Docker image with a name of your choice if you haven't
```shell
docker build --tag qa-api .
```
5. Spin up a server
```shell
docker run -d -p 5000:5000 --name qa-api qa-api
```
6. Try accessing [http://127.0.0.1:5000](http://127.0.0.1:5000) with a valid route