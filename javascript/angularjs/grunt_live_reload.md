## Live Reload configuration for grunt
1.  Install  [grunt-connect-proxy](https://github.com/drewzboto/grunt-connect-proxy)

2. Configure middleware.
```
//The actual grunt server settings
connect: {
  options: {
    port: 9000,
    // Change this to '0.0.0.0' to access the server from outside.
    hostname: 'localhost',
    livereload: 35729
  },
  proxies: {
    context: '/',
    host: 'localhost',
    port: 3000,
    https: false,
    changeOrigin: true
  },
  livereload: {
    options: {
      open: true,
      base: [
        '.tmp',
        '<%= yeoman.app %>'
      ],
      middleware: function (connect, options) {
        var middlewares = [];
        var directory = options.directory || options.base[options.base.length - 1];

        // enable Angular's HTML5 mode
        middlewares.push(modRewrite(['!\\.html|\\.js|\\.svg|\\.css|\\.png$ /index.html [L]']));
        if (!Array.isArray(options.base)) {
          options.base = [options.base];
        }
        options.base.forEach(function(base) {
          // Serve static files.
          middlewares.push(connect.static(base));

        });

        middlewares.push(
          connect().use(
            '/bower_components',
            connect.static('./bower_components')
          )
        )

        // Setup the proxy
        middlewares.push(require('grunt-connect-proxy/lib/utils').proxyRequest);

        // Make directory browse-able.
        middlewares.push(connect.directory(directory));

        return middlewares;
      }
    }
  },
  test: {
    options: {
      port: 9001,
      middleware: function (connect) {
        return [
          modRewrite(['^[^\\.]*$ /index.html [L]']),
          connect.static('.tmp'),
          connect.static('test'),
          connect().use(
            '/bower_components',
            connect.static('./bower_components')
          ),
          connect.static(appConfig.app)
        ];
      }
    }
  },
  dist: {
    options: {
      open: true,
      base: '<%= yeoman.dist %>'
    }
  }
}
```
