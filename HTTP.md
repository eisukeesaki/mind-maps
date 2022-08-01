# HTTP

```text

the web
    HTTP
        HTML
        CSS
        JavsScript
            web APIs
HTTP
    properties
        extensible by agreement between client and server
            about new header's semantics
                example
                    Set-Cookie and Cookie header field
                        enables stateful communication over stateless communication protocol
        does not require the underlying protocol to be connection-based
        requires underlying connection to be reliable
            relies on
                TCP
                QUIC
    features controllable with HTTP
        session
            HTTP cookies allow servers to link requests with state of server 
            useful for allowing user configuration of output
        caching
            how resources are cached can be controlled by HTTP
                server can instruct proxies and clients
                    what to cache
                    how long to cache
                clients can instruct intermediate cache proxies to ignore cached resources
        authentication
            with use of
                HTTP cookies
                ?WWW-Authenticate header
        ?relaxing the origin constraint
        ?proxy and tunneling
    HTTP flow
        open TCP connection
            new
                one
                several
            reuse existing connection
        send HTTP message
            GET / HTTP/1.1
            Host: www.example.org
        read response sent by server
            HTTP1.1 200 OK
            Date: <date>
            Content-Length: 1324
            Content-Type: text/html
            
            <!DOCTYPE html> ...
        close or reuse TCP connection
    HTTP message exchange
        before client and server can exchange HTTP messages, a TCP connection must be established
            HTTP/1.0
                opens separate TCP connections for each request/reponse pair
            HTTP/1.1
                pipelining
                    allows several requests to be sent without waiting for the first respnose to be fully received
                persisting connections
                    Connection header field
                        partially controll TCP connections
            HTTP/2
                multiplexes messages over a single TCP connection
    is
        protocol
            communication
                application layer
            model
                client-server
                    components of HTTP-based systems
                        communicates by exchanging HTTP messages
                        client
                            user agent
                                is
                                    tool that acts on behalf of user
                                browsers
                                cURL
                            proxy servers
                            roles
                                initiates
                                    requests
                                        is
                                            message sent by client
                                        client is always the entity initiating requests
                        server
                            roles
                                responds to
                                    requests
                                        is
                                            message sent by server
                                serves resources
                                    hypertext documents
                            virtually appears as single entity
                                can be cluster of servers which runs multiple instances of servers
                                    which may be communicating with other cluster of servers
                        proxies
                            functions
                                caching
                                load balancing
                                authentication
                                logging
                                filtering
    used for
        transmitting hypermedia
    backgrounds
        originally designed for communication between servers and clients
    properties
        unidirectional
            any data sent from server to client must be first requested from client
    HTTP request
        messages sent by the client to initiate an action on the server
    HTTP messages
        HTTP/1 and HTTP1.1 messages
            human readable
        HTTP/2 messages
            embedded into a frame
                binary structure
            allows optimizations
                header compression
                multiplexing
        request
            structure
                head
                    start-line
                        HTTP method
                            describes the action to be performed
                            verbs
                                GET
                                POST
                                PUT
                                DELETE
                                CONNECT
                                TRACE
                                PATCH
                            nouns
                                HEAD
                                OPTIONS
                        target
                            URL
                                absolute path of
                                    protocol
                                    port
                                    domain
                            format varies between HTTP methods
                                origin form
                                    is
                                        most common form
                                    URL
                                        /dir/file.ext
                                    query strings
                                        ?key=value
                                absolute form
                                    is
                                        mostly used
                                            with GET when connected to a proxy
                                    complete URL
                                        GET https://developer.mozilla.org/en-US/docs/Web/HTTP/Messages HTTP/1.1
                                authority form
                                    consists of
                                        domain name
                                        port number (optional)
                                    CONNECT developer.mozillla.org:80 HTTP/1.1
                                asterisk
                                    used with
                                        OPTIONS
                                    represents the server as a whole
                                    OPTIONS * HTTP/1.1
                        protocol version
                            HTTP/1.0
                            HTTP/1.1
                            HTTP/2
                    header
                        request headers
                            Host
                            User-Agent
                            Set-Cookie
                        general headers
                            Connection
                            Upgrade-Insecure-Requests
                        representation headers
                            Content-Type
                            Content-Length
                payload
                    body
                        often used with POST
                        Single-resource
                        Multiple-resource
                            HTML Forms
        response
            status(start) line
                protocol version
                    HTTP/1.0
                    HTTP/1.1
                    HTTP/2
                status code
                    Informational responses (100–199)
                    Successful responses (200–299)
                    Redirection messages (300–399)
                    Client error responses (400–499)
                    Server error responses (500–599)
                status text
                    OK
                    Found
                    Not Found
                    Internal Server Error
            header
                response
                    Vary
                    Accept-Ranges
                representation
                    Content-Encoding
                    Content-Type
                    Last-Modified
                general
                    Connection
                    Date
                    Transfer-Encoding
            body
                Single-resource
                    known length
                    unknown length
                Multiple-resource
                    1st section of info
                    Nth section of info
    HTTP sessions
        what it is
            series of requests and responses associated with a particular user
            allows a state to be maintained between application server and user agents
                use cases
                    maintain
                        an authentication state
                        other states
                if effect, it creates a stateful protocol on top of HTTP
        secret
            key used to sign session identifier
        session data
            association of user's account information and session identifier
                session identifier
                    saved on
                        server
                        backend database
                        client's cookie
            storage location
                backend database
                    sessions table
                    centralized maner
                        server has full control
                    does not act against distribution of servers(i.e scaling)
                    requires extra hop
                        relatively slow
                server memory
                    fast
                        does not require hop to backend database
                    scaling issues
                        scaling
                            distribution of server load
                                having multiple server instances across different computing resources
                                    distribution of server instances
                        session being stored on one particular server act against scaling of backend server
                client-side
                    decentralized manner
                    methods for achievement
                        use of
                            JWT
                                means of representing claims to be transferred between two parties
                    easy to implement
                        no need to store, fetch, process on server side
                    server cannot immediately revoke/invalid user
        transmission channel
            application layer
                HTTPS
        libraries
            express-session
                session middleware
                session()
                    creates new session middleware
            connect-pg-simple
                API used to abstract session store management
                designed for PostgreSQL
    APIs based on HTTP
        XMLHttpRequest
        Fetch API
            
project ideas to understnad HTTP
    build web crawler

```

## Resources
- [HTTP | MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP)
