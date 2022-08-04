[#](#) Passport.js

```text

Passport
    framework that encapsulates authentication functionality of web APIs
        Strategies
            implements
                authentication mechanisms
                    functionalities
                        credentials
                            encode
                            verify
            packaged strategies
                username & password
                OAuth 2.0
                OpenID Connect
                ...
        used as middleware within web application servers
            app.METHOD("/login")
                passport.authenticate(strategyName[, options][, callback])
        how to implement
            Sign in with Google integrated within Express application
                install Passport
                install Strategy
                configure Strategy
                    instantiate (new) Strategy
                        constructor
                            provide
                                options
                                ?callback function that encodes and verifies credentials
                                    verify(accessToken[, refreshToken], profile, done) callback function
                                        recieves accesstoken
                                        done()
                                            sets authenticated user to req.user
                        example
                            const strategyOptions = {
                              clientID: GOOGLE_CLIENT_ID,
                              clientSecret: GOOGLE_CLIENT_SECRET,
                              callbackURL: "http://example.com/auth/google/redirect"
                            }
                            function verify(accessToken, refreshToken, profile, cb){
                              User.findOrCreate({ googleId: profile.id }, function (err, cb) {
                                return cb(err, user);
                              });
                            }
                            const googleStrategy = new GoogleStrategy(strategyOptions, verify);
                            passport.use(googleStrategy);
                    define and provide to passport instance
                        function that serialize and deserialize users into and out of login sessions
                            invoked whenever req.login() and passport.authenticate() is called
                                should call done(null, serializedUser)
                                    passport.serializeUser(function([req ,]user, cb))
                                        invoked whenever ___ is called
                                            passport.authenticate()
                                            req.login()
                                        sets req.session.passport.user = serializedUser
                                        if multiple serializers are passed, they are called in order
                                    passport.deserializeUser(fn(req, serializedUser, cb))
                                        serializeUser == req.session.passport.user
                                        ?if session user no longer exist in database
                                            fn will passed a null or false to serializeUser
                                    passport.serializeUser(function(user, done) {
                                        done(null, user.id);
                                    });              │
                                                     │ 
                                                     │
                                                     └─────────────────┬──→ saved to session
                                                                       │    req.session.passport.user = {id: '..'}
                                                                       │
                                                                       ↓           
                                    passport.deserializeUser(function(id, done) {
                                                       ┌───────────────┘
                                                       │
                                                       ↓ 
                                        User.findById(id, function(err, user) {
                                            done(err, user);
                                        });            └──────────────→ user object attaches to the request as req.user   
                                    });
                                        
                register Strategy
                    passport.use(strategy)
                instantiate Passport class
                    require()
                mount Passport to middleware stack
                    app.use()
                        passport.initialize()
                            returns middleware
                                sets req._passport
                                    used by Passport
                mount session middleware
                    app.use()
                        initialize
                            express-session
                                ___ ___ cookie
                                    reads from
                                    writes to
                mount Passport's session support to middleware stack
                    app.use()
                        passport.session()
                            runs
                                built-in SessionStrategy
                                    calls
                                        deserializeUser(session.passport.user, done)
                            returns middleware
                                reads user out of session
                                    if user found
                                        sets req.user = deserializeUser
                                    else
                                        do nothing
                            does not take options
                            equal
                                app.use(passport.session)
                                app.use(passport.authenticate("session"))
                                    uses built-in session Strategy
                authenticate users
                    passport.authenticate(strategyName[, options][, callback])
                        what does it do
                            authenticate requests
                        logic flow
                            if successfully authenticated
                                set req.user to authenticated user
                                establish login session
                                    (automatically )invokes req.login(user, callback)
                                        assign user to req.user
                                            upon successful authentication
                                call next middleware in stack
                            else
                                send 401 and end [request response](request-response) cycle
                        returns middleware
                            runs strategies 
                                if successful authentication
                                    sets req.user
                            if no options or callback is provided and authentication fails
                                writes 401 to response header
                        adds helper functions to req object
                            login(user, callack(error))
                            logout(callback(error))
                                delete login session
                                    remove req.user 
                                        if there is any
                            isAuthenticated()
                        parameters
                            strategyName
                                can be array
                                    first Strategy to succeed, fail, redirect, or error will stop the chain
                            options
                                will be passed on to Strategy
                                one can pass callbackURL to an OAuth Strategy as an option
                                list
                                    successRedirect
                                        path to redirect to on a success.
                                    failureRedirect
                                        path to redirect to on a failure (instead of 401).
                                    failureFlash
                                        True to flash failure messages or a string to use as a flash message for failures (overrides any from the Strategy itself).
                                    successFlash
                                        True to flash success messages or a string to use as a flash message for success (overrides any from the Strategy itself).
                                    successMessage
                                        True to store success message in req.session.messages, or a string to use as override message for success.
                                    failureMessage
                                        True to store failure message in req.session.messages, or a string to use as override message for failure.
                                    session
                                        boolean, enables session support (default true)
                                    failWithError
                                        On failure, call next() with an AuthenticationError instead of just writing a 401.
                                    ?...
                            callback
                                function(err, user, info)
                        example of usage
                            app.post("/login/password",
                              passport.authenticate("local", { failureRedirect: "/login", failureMessage: true }),
                              function (req, res) {
                                res.redirect("/~" + req.user.username);
                              }
                            );

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

## resources
- [Official Documentation](https://www.passportjs.org/concepts/authentication)
- [Passport: The Hidden Manual](https://github.com/jwalton/passport-api-docs)
