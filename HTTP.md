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

```

