# The `src/app/home` Directory

## Overview

```
src/
  |- app/
  |  |- home/
  |  |  |- account.js
  |  |  |- home.less
  |  |  |- account.spec.js
  |  |  |- home.tpl.html
```

- `account.js` - defines the module.
- `home.less` - module-specific styles; this file is imported into
  `src/less/main.less` manually by the developer.
- `account.spec.js` - module unit tests.
- `home.tpl.html` - the route template.

## `account.js`

This boilerplate is too simple to demonstrate it, but `src/app/home` could have
several sub-folders representing additional modules that would then be listed
as dependencies of this one.  For example, a `note` section could have the
submodules `note.create`, `note.delete`, `note.search`, etc.

Regardless, so long as dependencies are managed correctly, the build process
will automatically take take of the rest.

The dependencies block is also where component dependencies should be
specified, as shown below.

```js
angular.module( 'ngBoilerplate.home', [
  'placeholders',
  'titleService'
])
```

Each section or module of the site can also have its own routes. AngularJS will
handle ensuring they are all available at run-time, but splitting it this way
makes each module more self-contained.

```js
.config([ '$routeProvider', function config( $routeProvider ) {
  $routeProvider.when( '/home', {
    controller: 'HomeCtrl',
    templateUrl: 'home/home.tpl.html'
  });
}])
```

And of course we define a controller for our route, though in this case it does
nothing.

```js
.controller( 'HomeCtrl', [ '$scope', 'titleService', function HomeController( $scope, titleService ) {
  titleService.setTitle( 'Home' );
}]);
```