# daiv-json-server
JSON server using JSONPlaceholder

Reference Link: https://github.com/typicode/json-server

https://my-json-server.typicode.com/ubuntu-prasad/daiv-json-server

Use your own data
Fork it and change db.json values or create a repo with a db.json file.

#Mockend.com Fake API

Refer url for details https://docs.mockend.com/

#Installation

Install Mockend GitHub app on your repo. For the rest of the docs, we'll consider it's `org/repo`.

Create a `.mockend.json` file to describe your API.

#Configuration

Supported types are: `string`, `int`, `boolean` and `date`.

You can also describe `has many` and `belongs` to relations.

###For example:

.mockend.json
```json
{
  "Post": {
    "title": "string",
    "views": "int",
    "published": "boolean",
    "createdAt": "date",
    "comments": "Comment[]"
  },
  "Comment": {
    "body": "string",
    "post": "Post"
  }
}
```

#Routes

For REST, based on the previous config, the following routes will be created:
```
GET https://mockend.com/ubuntu-prasad/daiv-json-server/posts
GET https://mockend.com/ubuntu-prasad/daiv-json-server/posts/<id>
GET https://mockend.com/ubuntu-prasad/daiv-json-server/comments
GET https://mockend.com/ubuntu-prasad/daiv-json-server/comments/<id>
```  
Routes can take query parameters, see below.

GraphQL, will be available at:
```
https://mockend.com/ubuntu-prasad/daiv-json-server/graphql
```
Mockend supports Git branches, you can therefore have multiple mock APIs for different features on the same repo.

Simply add `tree/:branch_name` to your URL, for example:
```
/ubuntu-prasad/daiv-json-server/tree/my-awesome-feature/graphql
```
#Queries

###REST

Query parameters can be used to filter, sort and paginate lists:

- `_eq` `_ne`
  - equal, not equal
- `_gt` `_lt`
  - greater than, lower than
- `_order`
  - sort data (`asc` `desc`)
- `limit` `offset`
  - use them to paginate your results

For example:
```
GET /posts?date_order=desc

GET /posts
    ?views_gt=10
    &published_eq=true
    &views_order=desc
    &limit=5
```

#GraphQL

A GraphiQL interface, with specific documentation for your API, can be found directly at:
```
https://mockend.com/ubuntu-prasad/daiv-json-server/graphql
```
