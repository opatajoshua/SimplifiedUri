## A simple Flutter / Dart Utility class for converting complex or nested objects to uri and query strings

# Example1 
``` dart
final params = {
  'name': 'John',
  'columns': ['firstName', 'lastName']
  'ageRange':{
    'from': 12,
    'to': 60,
    'someInnerArray': [1,2,3,5]
  }
};
final Uri uri = SimplifiedUri.uri('www.api.mysite.com/users', params);
final headers = {HttpHeaders.contentTypeHeader: 'application/json'};
final response = await http.get(uri, headers: headers);
```

## Example 2 using objectToQueryString() methis
``` dart
final params = {
  'name': 'John',
  'columns': ['firstName', 'lastName']
  'ageRange':{
    'from': 12,
    'to': 60,
    'someInnerArray': [1,2,3,5]
  }
};
final queryString = objectToQueryString(param);
final Uri uri = 'www.api.mysite.com/users?$queryString';
final headers = {HttpHeaders.contentTypeHeader: 'application/json'};
final response = await http.get(uri, headers: headers);

```