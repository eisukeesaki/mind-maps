# REST API

```text

REST
    architectural style
        distributed hypermedia systems
    REST API
        consists
            assembly of interlinked resources
                resource model
        principles
            uniform interface
                identification of resources
                    interface must uniquely identify each reseource
                        involved in the interaction between the client and the server
                manipulation of resources through representations
                self-descriptive messages
                hypermedia as the engine of application state
            client-server
                enforces separation of concerns
                    helps client and server components to evolve independently
                    separation of UI concerns and data storage concerns
                        improves portability of UI across multiple platforms
                developers must make sure that the interface/contract between the client and the server does not break
            stateless
                each request from the client to the server
                    must contain all information necessary to understand and complete the request
                server cannot take advantage of previously stored context information on the server
            cacheable
                response should label itself as cacheable or non-cacheable
            layered system
                allows an architecture to be composed of hierarchical layers by contraining component behavior
                    each component cannot see beyond the immediate layer they are interacting with
            optional
                code on demand
        resource
            what
                any concept that might be the target of an author's hypertext reference
                data
                functionality
                examples
                    users of the system
                    customer orders
                    network devices
                    image
                    temporal service
                    non-virtual objects
                        human
            resource representation
                state of resource
                consists
                    data
                    metadata
                    hypermedia links
                exchanged using standardized interace and protocol
                    HTTP commonly used
            is primary data representation
                naming practices
                    use
                        nouns
                            thing
                        /
                            indicate hierarchical relationships
                                api.example.com/users/{id}/orders/{id}
                        -
                            improve readability of names in long path segments
                                api.example.com/very-long-path-segment
                        lower case letters
                        query component to filter URI collection
                            based on specific resource attribute
                                filters
                                    sort
                                    filter
                                    limit
                            don't create dedicated API
                                for
                                    sorted
                                    filtered
                                    limited
                                alternate solution
                                    enable filtering capabilities in resource collection API
                                              ├─ sorting
                                              ├─ filtering
                                              └─ limiting
                                        pass input parameters
                                            as query parameters
                    do not use
                        /
                            reasons
                                adds no semantic value
                                may confuse
                            example
                                api.example.com/users/
                        _
                        file extensions
                        CRUD function names
                units
                    singleton
                        example
                            /user
                    collection
                        example
                            /users
                    sub-collection
                        example
                            /users/{userId}/orders
                archetypes
                    architype
                        models a concept
                        an original that has been imitated
                    document
                        attributes
                            akin to object instance or database record
                            single resource inside resource collection
                        naming practices
                            use singular
                        exmaple
                            api.example.com/user-management/users/{id}
                    collection
                        attribute
                            server-managed directory of resources
                            consists of other resources
                        functions
                            chooses what to contain
                            decides URIs of contained resources
                        naming practices
                            use plural
                        example
                            api.example.com/user-management/users/{id}/orders/{id}
                    store
                        attributes
                            never generates new URIs
                            client-managed resource repository
                        stored resource
                            each has URI
                        naming practices
                            use plural
                        example
                            api.example.com/song-management/users/{id}/playlists
                    controller
                        procedural concept
                        naming practices
                            use verb
                                exception
                                    use nouns for all other archetypes of resources
            identified
                Uniform Resource Identifier
            hypermedia
                media type
                    data format of representation
                    identifies specifications that defines how a representation is to be processed
                hypertext
                    does not need to be
                        HTML
                        XML
                        JSON
                hypertext or hypermedia means the simultaneous presentation of information and controls such that the information becomes the affordance through which the user obtains choices and selects action
            self-descriptive
                clients should be able to act based on the media type associated with the resource
            resource methods
                used to perform desired transition between two states of any resource
                != HTTP methods
            
                

```

## external links
* [resource naming](https://restfulapi.net/resource-naming/)
