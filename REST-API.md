# REST API

```text

REST
    architectural style
        distributed hypermedia systems
    REST API
        resource
            any concept that might be the target of an author's hypertext reference
            abstraction of information
            examples
                users of the system
                customer orders
                network devices
                image
                temporal service
                non-virtual objects
                    human
            primary data representation
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

```

## external links
* [resource naming](https://restfulapi.net/resource-naming/)
