## Notes

When using HTML5 Mode:
```
$locationProvider.html5Mode(true)
```

Include the following snippet in your GruntFile:
```
var modRewrite = require('connect-modrewrite');

livereload: {
    options: {
        open: true,
        middleware: function (connect) {
            return [
                modRewrite(['^[^\\.]*$ /index.html [L]']),
                connect.static('.tmp'),
                connect().use(
                    '/bower_components',
                    connect.static('./bower_components')
                ),
                connect.static(appConfig.app)
            ];
        }
    }
},
```
