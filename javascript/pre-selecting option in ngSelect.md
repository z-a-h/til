# Pre-selecting Option in ngSelect

When using ng-select for a select input use ng-options to render a list of options. `select as` can be used to bind the result of the select to the model and the value of the `<select>` and `<option>` elements will be either the index or property name of the value in the collection.

With this array 
```javascript
$scope.documents = [{
  id: 1,
  name: "Bob",
  subDoc: {text: "text"}
  },{
  id: 2,
  name: "John",
  subDoc: {text: "text"}
  }
}];
This select 
```
`<select ng-options="document as document.name for document in documents track by document.id" ng-model="selectedDocument"></select>`
return this
```javascript
$scope.selectedDocument = $scope.documents[0]
``` 

However, the below won't work.
`<select ng-options="document.subDoc as document.name for document in documents track by document.id" ng-model="selectedDocument"></select>`
It returns: `$scope.selectedDocument = $scope.documents[0].subDoc` which is undefined

Additionaly if you want to pre-select an option in a select from an element not in the options, the model must be the same format as the items in the options
```javascript
$scope.user = {
  id: 1,
  name: Bob,
  document_id: 1
}
```
`<select ng-options="document as document.name for document in documents track by document.id" ng-model="user.document_id"></select>` 

This will not pre-select `$scope.documents[0].id`. The value of the ng-model must be the same format as the options.