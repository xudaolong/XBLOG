# jquery

```
$.ajax({
  url: '/myEndpoint.json',
  success: function ( data, status ) {
    $('ul#log').append('<li>Data Received!</li>');
  }
});

<ul class="messages" id="log">
</ul>
```

# angular

```
$http( '/myEndpoint.json' ).then( function ( response ) {
    $scope.log.push( { msg: 'Data Received!' } );
});

<ul class="messages">
    <li ng-repeat="entry in log">{{ entry.msg }}</li>
</ul>
```
