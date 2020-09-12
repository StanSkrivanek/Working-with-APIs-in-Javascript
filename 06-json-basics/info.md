# JSON

JSON are data written with same syntax as object literal, except that in JSON file properties have to be surrounded with quotes (double quotes)

## index_1

Load JSON object from inline script 


```json
{
  "name": "John",
  "age": 15,
  "address": {
    "city": "London",
    "street": "Baker str. 15"
  },
  "hobbies": ["football", "music", "drawing"]
}
```

## index_2

Load JSON from project file


## index_3

Load JSON data from external API 


### short explanation

Principle is to fetch data from another website that have API endpoints

```js
const url = "some API endpoint";

fetch(URL);
```
