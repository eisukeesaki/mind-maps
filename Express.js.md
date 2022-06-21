# Express.js

```text

Express.js
    routing
        how app's endoints respond to requests
    middleware stack
        app._router.stack
    res.render()
        render view and sends rendered HTML string to client
        res.locals
            local variables for views
    express instance
        ...
        mountpath
        _router
            params {}
            _params []
            stack [ [Layer], [Layer], ... ]
    pass control to next middleware in stack
        next()
        ?next('route')

```

