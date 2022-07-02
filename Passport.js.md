# Passport.js

```text

Passport.js
    /lib
        /middleware
            initialize(passport, options)
            authenticate(passport, name, options, callback)
        /framework
            connect.js
                expose
                    /middleware/initialize
                    /middleware/authenticate
        /http
            req.login = function(user, options, done)
            req.logout = function(options, done)
            req.isAuthenticated = function()
            req.isUnauthenticated = function()
        SessionManager(options, serializeUser)
            logIn(req, user, options, cb)
            logOut(req, options, cb)
        SessionStrategy(options, deserializeUser)
            authenticate(req, options)
        Authenticator() = Passport
            init()
            use(name, strategy)
            unuse(name)
            framework(fw)
            initialize(options)
            authenticate(strategy, options, callback)
            authorize(strategy, options, callback)
            session(options)
            serializeUser(fn, req, done)
            deserializeUser(fn, req, done)
            transformAuthInfo(fn, req, done)
            _strategy(name)


passport-google-oauth20
    function Strategy(options, verify)
        options
        verify
        OAuth2Strategy.call(this, options, verify);
req
    req._passport
    req.session.passport
?
    ?verify(?)
        ?done(?)


```

