# HTTP

```text

HTTP
    unidirectional
        any data sent from server to client must be first requested from client
    request
        messages sent by the client to initiate an action on the server
    HTTP/1.1 message
        request
            head
                start-line
                    method
                        description of the action to be performed
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
                        usually an URL
                        origin form
                            URL
                                /dir/file.ext
                            query strings
                                ?key=value
                        complete URL
                            https://developer.mozilla.org/en-US/docs/Web/HTTP/Messages
                    protocol version
                        HTTP/1.1
                        HTTP/2
                header
                    request
                        Host
                        User-Agent
                        Accept-…
                    general
                        Connection
                        Upgrade-Insecure-Requests
                    representation
                        Content-Type
                        Content-Length
            payload
                body
                    Single-resource
                    Multiple-resource
                        HTML Forms
        response
            status(start) line
                protocol version
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
        a solution
            means to eliminate the need for clients to make authentication requests every time before they make any other requests
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
            
```

