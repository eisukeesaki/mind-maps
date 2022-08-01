# World Wide Web

```text

World Wide Web
    source document
        Hypertext Markup Language
            anchor text
                hypertext
                    hyperlink
                        URI
    resource
        is
            target of HTTP request
            identified by
                Uniform Resource Identifier (URI)
                    └─ consistent within a defined scope
                    Uniform Resource Locator (URL)
                        A.K.A.
                            web address
                        examples
                            http://www.example.com:80/path/to/myfile.html?key1=value1&key2=value2#SomewhereInTheDocument
                    Uniform Resource Name (URN)
                        identifies resource by name is particular namespace
                        examples
                            urn:isbn:9780141036144
                            urn:ietf:rfc:7230
                    syntax
                        structure
                            protocol://authority:port/path?query#fragment
                        protocol (or scheme)
                            http
                            https
                            ftp
                            urn
                            file
                            data
                            ssh
                            ...
                            examples
                                https://
                        authority
                            authority that governs the domain namespace
                            domain name
                            indicates which web server is being requested
                            examples
                                www.example.com
                        port
                            standard ports can be ommited
                                HTTP
                                    80
                                HTTPS
                                    443
                            examples
                                :80
                        path
                            path to resource on web server
                            examples
                                /path/to/index.html
                        query
                            list of key=value pairs
                            parameters provided to web server
                            used by web servers to make responses
                            specified by web server developers
                            examples
                                ?orderBy=dateAsc
                                ?filterBy=inStock
                        fragment
                            anchor to another part of resource itself
                            never sent to web servers
                    
        

```

