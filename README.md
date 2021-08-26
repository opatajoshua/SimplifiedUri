## A simple Flutter / Dart Utility class for converting complex or nested objects to uri and query strings

you can follow the [the article on how this class was built](https://jol.hashnode.dev/flutter-convert-complex-objects-nested-maps-lists-to-a-url-query-string) and add suggestions

# Example1 
``` dart
final params = {
  'name': 'John',
  'columns': ['firstName', 'lastName'],
  'ageRange': {
    'from': 12,
    'to': 60,
  },
  'someInnerArray': [1,2,3,5]
};
final Uri uri = SimplifiedUri.uri('http://api.mysite.com/users', params);
final headers = {HttpHeaders.contentTypeHeader: 'application/json'};
final response = await http.get(uri, headers: headers);
```
output
```
http://api.mysite.com/users?name=John&columns%5B%5D=firstName&columns%5B%5D=lastName&ageRange%5Bfrom%5D=12&ageRange%5Bto%5D=60&someInnerArray%5B%5D=1&someInnerArray%5B%5D=2&someInnerArray%5B%5D=3&someInnerArray%5B%5D=5
```

## Example 2 using the objectToQueryString() method
``` dart
final params = {
  'name': 'John',
  'columns': ['firstName', 'lastName'],
  'ageRange': {
    'from': 12,
    'to': 60,
  },
  'someInnerArray': [1,2,3,5]
};
final queryString = objectToQueryString(param);
final Uri uri = 'http://api.mysite.com/users?$queryString';
final headers = {HttpHeaders.contentTypeHeader: 'application/json'};
final response = await http.get(uri, headers: headers);

```

same output
```
http://api.mysite.com/users?name=John&columns%5B%5D=firstName&columns%5B%5D=lastName&ageRange%5Bfrom%5D=12&ageRange%5Bto%5D=60&someInnerArray%5B%5D=1&someInnerArray%5B%5D=2&someInnerArray%5B%5D=3&someInnerArray%5B%5D=5
```
