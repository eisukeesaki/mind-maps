# REST

```text

notes - Roy Fielding's paper
    Network-based Architectural Styles
    ##################################
        hierarchical styles
        ===================
            Client-Server (CS)
            ------------------
                architectural style for network-based applications
                    implementation of separation of concerns
                architecutral components
                    server
                        a reactive process
                            offers set of services
                        waits for requests to be made and then reacts to them
                            listens for requests upon services
                            rejects or performs request and sends response to client
                        common properties
                            a non-terminating process
                            provides service to more than one client
                    client
                        a triggering process
                            consumes services
                        makes requests that triggers reactions from servers
                            sends requests to server via connector
            Layerd System (LS)
            ------------------
                is
                    organized hierarchically
                provides service
                    to layer above itself
                uses services
                    of layer below itself
                use within networked-based systems is limited
                    to its combination with the client-server style
                        to provide Layere-Client-Server
                            Layered-Client-Server (LCS)
                            ---------------------------
                                adds ___
                                    ___
                                        proxy
                                            acts as a shared server for one or more client components
                                            roles
                                                takes request
                                                forwards request
                                                    to server components
                                                can translate requests
                                        gateway
                                            appearts to be normal server
                                                to
                                                    ___ that request its services
                                                        ___
                                                            clients
                                                            proxies
                                            roles
                                                takes request
                                                forwards request
                                                    to inner-layer server components
                                                can translate requests
                                        is
                                            additional mediator server components
                                            solution
                                                to managing identity
                                                    in a large scale distributed system
                                                        where complete knowledge of all servers would be prohibitively expensive
                                                    the solution
                                                        instead of trying to store complete knowlege of all servers,
                                                            servers are organized in layers
                                                                such that rarely used services are handled by intermediaries
                                                                    rather than directly by each client
                                        enables
                                            features of the system
                                                load balancing
                                                security checking
                                    to client-server style
                implementation examples
                    TCP/IP
                    OSI protocol stacks
                    hardware interface libraries
                induces disadvantages
                    increased ___
                        ___
                            overhead
                            latency
                        to the processing of data
                        induces
                            reduced user-percieved performance
        mobile code styles
        ==================
            Code on Demand (COD)
            --------------------
                code
                    is
                        set of instructions on how to process a given resource
                client component
                    has access to resources
                        but not the know-how to process them
                    makes a request
                        to get code representing the know-how to process the resource
                    executes the code to process the resource locally
                                   └─ know-how
                induces advantages
                    ability to add features to a deployed client
                        induces advantages
                            improved ___
                                ___
                                    extensibility
                                    configurability
                                    user-percieved performance
                                    efficiency
                                    scalability of server
                                        induced by
                                            enabling the server to off-load work to the client
                                                that would otherwise consumed its resources
                                when the code can adapt its actions to the client's environment
                                    and interact with the user locally
                                        rather than through remote interactions
                        induces disadvantages
                            reduced simplicity
                                due to the need to manage the evaluation environment
                                may be compensated
                                    as a result of simplifying the client's static functionality
                            lack of visibility
                                induced by
                                    server sending code instead of simple data
                                induces
                                    deployment problems
                                        if the client cannot trust the servers
    perspectives on the process of architecutral designs
        a perspective
            purposes the process
                differentiate the design space
                allow to flow forces that influence system behavior
                    naturally
                    in harmony with the system
            process
                designer
                    starts with system needs as a whole without constraints
                    ___ constraints
                        incrementally 
                        ___
                            identifies
                            applies
                        to elements of the system
            puts emphasis on
                restraint
                understanding of the system context
            used to deploy REST
    Representational State Transfer (REST)
    ######################################
        how the paper describes the reaionalte behind the web architecure (REST)
            by describing
                the process of designing a network-based web architecure 
                    adding one constraint at a time
                the specific constraints that compose the architectural style
        is
            network-based architecutral style
                used for
                    distributed hypermedia systems
                property
                    hybrid-style
                        style is derived from several other network-based architectural styles
            consists of
                set of architecutral constraints
                    chosen for the properties they induce
                        on candidate architectures
        REST constraints
        ================
            null-style
            ----------
                empty set of constaints
                no distinguished boundaries between architecutral components
            Client-Server 
            -------------
                'separation of concerns'
                    concerns
                        user interface 
                        data storage
                    advantages
                        portability of user interace across multiple platforms
                        scalability
                            because
                                can simplify server components
                        allows architecutral components to evolve independently
            stateless
            ---------
                requirements
                ^^^^^^^^^^^^
                    each request must contain
                        all of the information necessary to understand the request
                    cannot take advantage of any stored context on the server
                        session state is kept entirely on the client
                advantages
                    visibility
                        because
                            monitoring system does not have to look beyond a single request datum to determine the full nature of the request
                    reliability
                        because
                            eases that task of recovering from partial failures
                    scalability
                        because
                            does not put pressure on data storage space
                                especially in-memory storage
                            simplifies implementation
                                becaues
                                    server does not have to manage resource usage across requests
                disadvantages
                    increased per-interaction overhead
                    reduced control over consistent application behavior
                        induced by
                            placing application states on the client-side 
            cache
            -----
                purpose
                    to improve network efficiency
                requirements
                ^^^^^^^^^^^^
                    response must indicate cacheability
                        labels (indication)
                            cachable
                            non-cacheable
                client-cache-stateless-server style
                    cacheable response
                        client cache reuses response data
                            for ___ requests
                                ___
                                    later
                                    equivalent
                induces advantages
                    improved
                        efficiency
                        scalability
                    elimination of some interactions
                        degree
                            partially
                            completely
                        results in
                            improved user perceived performance
                                induced by
                                    decreased average latency of a series of interactions
                trade-off
                    disadvantage
                        induces architecutral properties
                            decreased reliability
                                induced by
                                    significant difference between
                                        stale data within cache
                                        data that would have been obtained
                                            had the request been sent directly to the server
            uniform interface
            -----------------
                is
                    application of 'generality'
                        to
                            architecutral component interface
                    designed to increase efficiency
                        for common case of the Web
                interface constaints
                    is
                        constraints needed to guide the behavior of architecutral components
                    constaints
                    ^^^^^^^^^^
                        identification of resources
                        manipulation of resources through representations
                        self-descriptive messages
                        hypermedia as the engine of application state
                induces
                    advantages
                        simplified overall system architecture
                        improved visibility of interactions
                        independent evolvability
                            induced by
                                decoupling of
                                    architectural implementation
                                    service provided on the architecture
                    disadvantages
                        degrades efficiency
                            induced by
                                standardization of transferring methods
                                    of information
                            because the architecture does not
                                use transferring methods which is most appropriate for a specific application's need
            Layered System
            --------------
                allows an achitecture to be composed of
                    hierarchical layers
                how it is enabled
                    by restricting knowledge of the system
                        to ___ layer
                            ___
                                single
                                immediate
                layers
                    can be used to
                        encapsulate legacy services
                        protects new services from legacy clients
                    allows
                        security policies to be enforced
                            on data crossing the organizational boundary
                                as is required by firewalls
                intermediaries
                    can be used to
                        improve scalability
                            by
                                enabling load balancing of services
                                    across
                                        multiple networks
                                        processors
                simplifies architectural components
                    by
                        moving infrequently used functionality to a shared intermediary
                promotes substrate independence                           
                    induced by
                        placing bounds on the overall system complexity
                induces disadvantage
                    increased ___
                        ___
                            overhead
                            latency
                        to the processing of data
                        induces
                            reduced user-percieved performance
                        can be offset
                            for network-based systems that supports cache constraints
                            by the benefits
                                of shared caching
                                    at intermediaries
                induces architectural properties
                    by combination of ___
                        ___
                            layerd system
                            uniform interface constraints
                        data flows of hypermedia interaction can each be processed like a data-flow network
                            regardless of the fact that REST interaction is two-way
                        filter components can be selectively applied
                            to the data stream
                                in order to
                                    transform the content as it passes
            Code-on-Demand (COD)
            --------------------
                is
                    optional constraint
                    ^^^^^^^^^^^^^^^^^^^
                induces advantages
                    extension of client functionality
                        by
                            downloading and executing code
                                form of code
                                    applets
                                    scripts
                    simplification of clients
                        induced by
                            reduced number of features required to be pre-implemented
                induces disadvantages
                    reduced visibility
                ?architecture only gains benefit when they are known to be in effect for some realm of the overall system
            style derivitation summary
            --------------------------
        REST architecutral elements
        ===========================
            data elements
            -------------
            resources and resource identifiers
            ----------------------------------
            representations
            ---------------
            connectors
            ----------
            components
            ----------
        REST architecutral views
        ========================
            process view
            ------------
            connector view
            --------------
            data view
            ---------
                                
                
notes - REST Tutorial by Lokesh Gupta
    architectural style
        distributed hypermedia systems
    REST API
        how to design
            create object model
            create model URIs
            determine resource representations
            assign HTTP methods to URIs
            more to implement
                logging
                security
        is
            way to expose data from a server
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

* [Roy Fielding's paper](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)
* [REST API Tutorial by Lokesh Gupta](https://restfulapi.net)
