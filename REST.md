# REST

```text

notes - Roy Fielding's paper - second pass
    #########################################
    # Representational State Transfer (REST) #
    #########################################
        solution for
            problems
                how to design a distributed hypermedia system?
        definition
            an abstraction of the architectural elements within a distributed hypermedia system
            an hybrid architecutral style
                of other networked-based architecutral styles for distributed hypermedia systems
            a set of architecutral constraints which retain the software engineering principles guiding itself
        functions
            defines interaction constraints chosen to retain software engineering principles guiding REST
        properties
            contrasts software engineering principles guiding REST to the constraints of other architectural styles
            ignores the details of component implementation and protocol syntax
                in order to focuses on
                    the roles of components
                    the constraints upon components' interaction with other components
                    components' interpretation of significant data elements
            ?encompasses the fundamental constraints
                upon
                    components
                    connectors
                    data that define the basis of the Web architecture
            enforces stateless interactions between architecutral components
        mechanism
            elements
                constraints
                ###########
                    Null Style
                    ==========
                        definition
                            architectural style for network-based applications
                            empty set of constaints
                            no distinguished boundaries between architecutral components
                        solution for
                            problem
                                the process of architectural design used to develop REST needed something to start designing with
                        functionality
                            acts as a foundation of the REST architecture style
                    Client-Server
                    =============
                        definition
                            architectural style for network-based applications
                            an architecutral constaint intended to implement 'separation of concerns' of software engineering principles
                        solution for
                            problems
                                working with user interface concerns and data storage concerns within a single architectural component;
                                    complicates the architecure
                                    hinders components' independent evolution
                        mechanism
                            elements
                                client
                                ^^^^^^
                                    definitions
                                        a triggering process which consumes services
                                    roles
                                        functions
                                            initiates communication by making a request
                                            makes requests via connector to servers that triggers reactions from servers
                                    properties
                                        a component may include both client and server connectors
                                    example instances
                                        libwww
                                        libwww-perl
                                server
                                ^^^^^^
                                    definitions
                                        a reactive and non-terminating process which offers services to clients
                                    roles
                                        functions
                                            waits for requests to be made and then reacts to them
                                                operations
                                                    listens for requests upon services
                                                    rejects or performs request and sends response to client
                                            listens for connections and responds to requests in order to supply access to its services
                                    properties
                                        a component may include both client and server connectors
                                    example instances
                                        libwww
                                        Apache API
                                        NSAPI
                    Stateless
                    =========
                        definition
                            architectural style for network-based applications
                            an architecutral constaint that enforces architecutral components to make comprehensive requests/responses
                        solution for
                            problems
                                visibility
                                    how to create a system that allows monitoring systems to determine the full nature of the request without having to look beyond a single request datum
                                reliability
                                    how to create a system that eases the task of recovering from partial failures
                                scalability
                                    how to create a system that does not put pressure on the servers' data storage space
                        functions
                            enforces clients and servers to make comprehensive requests/responses
                            removes any need for the connectors to retain application state between requests
                            allows interactions to be processed in parallel without requiring that the processing mechanism understand the interaction semantics
                            allows an intermediary to view and understand a request in isolation
                            forces all of the information that might factor into the reusability of a cached response to be present in each request
                        mechanism
                            elements
                                constraints
                                ^^^^^^^^^^^
                                    each request must contain all of the information necessary for the connectors to understand the request
                                    a request cannot take advantage of any stored context on the server
                        properties
                            reduces consumption of physical resources improving scalability
                        induced disadvantages
                            increased per-interaction overhead
                            reduced control over consistent application behavior
                                induced by
                                    placing application states on the client-side 
                    Cache
                    =====
                        definition
                            architectural style for network-based applications
                            architecutral constraint intended to improve network efficiency
                        solution for
                            problems
                                how to improve network efficiency
                                how to improve user perceived performance
                                    how to decrease average latency of a series of interactions
                        functions
                            partially or completely eliminate some interactions
                            saves cacheable responses to current interactions so that they can be reused for later requested interactions
                            determine the cacheability of a response
                        mechanism
                            elements
                                requirements (constraints)
                                    response must indicate cacheability (reusability)
                                        labels
                                            cachable
                                            non-cacheable
                                    roles
                                        allows clients to determine the reusability of and accessibility to the reusable (cacheable) response data
                                interface
                                    properties
                                        is generic rather than specific to each resource
                                configurations
                                    default configuration
                                        response to a retrieval request is cacheable
                                        responses to other requests are non-cacheable
                        properties
                            can be located on the interface to a client or server connector
                            implemented within the address space of the connector that uses it
                            some cache connectors are shared
                            shared caching can be effective at reducing the impact of "flash crowds" on the load of a popular server, particularly when the caching is arranged hierarchically to cover large groups of users
                            shared caching can lead to errors if the cached response does not match what would have been obtained by a new request
                        purpose of use
                            by client
                                to reduce interaction latency
                                    by avoiding repetitive network communication
                            by server
                                to reduce interaction latency
                                    by avoiding repeated process of generating a response
                        induced disadvantages
                            ?decreased reliability
                                mechanism
                                    cause
                                        stale data within the cache differs significantly from the data that would have been obtained had the request been sent directly to the server
                        example instances
                            browser cache
                            Akamai cache network
                    Uniform Interface
                    =================
                        definition
                            an architectural style for network-based applications
                            ?an architecutral constraint ...
                        solution for
                            problems
                                how to simplify the overall system architecure and improve the visibility of interactions
                                how to encourage independent evolvability of architecutral components
                        functions
                            defines an uniform interface between architecutral components
                            decouples architecutral implementation from services provided on the distributed hypermedia system
                            ?applies the software engineering principle of generality to the component interface
                                ?wouldn't generality add restrictions and limitations?
                            increase efficiency for common case of the Web
                        mechanism
                            elements
                                constraints
                                -----------
                                    identification of resources
                                    manipulation of resources through representations
                                    self-descriptive messages
                                    hypermedia as the engine of application state
                                    roles
                                        guides the behavior of architecutral components
                                architecutral elements
                                ______________________
                                    data elements
                                    -------------
                                        definition
                                        solution for
                                            problems
                                                 when a link is selected, how to move information from the location where it is stored to the location where it will be used by
                                             solution
                                                elements
                                                    render the data where it is located and send a fixed-format image to the recipient
                                                    encapsulate the data with a rendering engine and send both to the recipient
                                                    send the raw data to the recipient along with metadata that describes the data type, so that the recipient can choose their own rendering engine
                                                REST components communicate by transferring a representation
                                                    of a resource in a format matching one of an evolving set of standard data types
                                                    selected dynamically based on the capabilities or desires of the recipient and the nature of the resource
                                                    that consists of instructions on how to process a given resource
                                                        in the standard data format of an encapsulated rendering engine
                                                            example
                                                                Java
                                                        but not always
                                        functions
                                            focuses on a shared understanding of data types with metadata, but limits the scope of what is revealed to a standardized interface
                                            hides the difference between the raw source and the representation behind the interace
                                            approximates the benefits of the mobile (Code on Demand) object style 
                                                sends a representation that consists of instructions in the standard data format of an encapsulated rendering engine
                                            gains the separation of concerns of the client-server style without the server scalability problem
                                            allows information hiding through a generic interface to enable encapsulation and evolution of services
                                            provide for a diverse set of functionality through downloadable feature-engines
                                        mechanism
                                            elements
                                                resource
                                                ^^^^^^^^
                                                    definitions
                                                        a key abstraction of information in REST
                                                        any information that can be named
                                                        the intended conceptual target of a hypertext reference
                                                        conceptual mapping to set of entities
                                                    functionality
                                                        ?provides 'generality' by encompassing many sources of information without artificially distinguishing them by type or implementation
                                                        allows late binding of the reference to a representation, enabling content negotiation to take place based on characteristics of the request
                                                        allows an author to reference the concept rather than some singular representation of that concept
                                                            thus removing the need to change all existing links whenever the representation changes (assuming the author used the right identifier).
                                                    mechanism
                                                        elements
                                                            constraints
                                                                use of resource identifiers to identify the particular resource involved in an interaction between components
                                                    properties
                                                        adds responsibility to naming authority that assigned the resource identifier
                                                            the naming authority must maintain the semantic validity of the mapping over time
                                                            relies on the author choosing a resource identifier that best fits the nature of the concept being identified
                                                    example instances
                                                        web service
                                                        API endpoint
                                                        Users
                                                        Orders
                                                    resource metadata
                                                    ^^^^^^^^^^^^^^^^^
                                                        definition
                                                            information about the resource that is not specific to the supplied representation
                                                        role
                                                            describes the resource metadata
                                                        properties
                                                            utilized on occasion
                                                        usecases
                                                            can be used to verify the integrity of a message
                                                        example instances
                                                            source link
                                                            alternates
                                                            vary
                                                    resource identifer
                                                    ^^^^^^^^^^^^^^^^^^
                                                        example instances
                                                            URI
                                                            URL
                                                            URN
                                                representation
                                                ^^^^^^^^^^^^^^
                                                    definition
                                                        a medium used to capture the current or intended state of the resource and transfer that between components
                                                        a sequence of bytes, plus representation metadata to describe those bytes
                                                    solution for
                                                        problems
                                                            how to capture the state of the resource and transfer them between components
                                                    functions
                                                        represents the current or intended state of the resource in a sequence of bytes, plus representation metadata to describe those bytes
                                                        indicates the state of the requested resource
                                                            current state
                                                            desired state
                                                        indicates value of some other resource
                                                            other resources
                                                                example instances
                                                                    a representation of;
                                                                        the input data within a client's query form
                                                                        some error condition for a response
                                                    form
                                                        data format
                                                            media type
                                                                properties
                                                                    design of it can directly impact the user-perceived performance of a distributed hypermedia system
                                                                example instances
                                                                    application/javascript
                                                                    application/json
                                                                    audio/mpeg
                                                                    image/png
                                                                    multipart/form-data
                                                                    text/html
                                                    properties
                                                        included in a message
                                                        processed by the recipient
                                                            according to the control data of the message and the nature of the media type
                                                        some are intended for automated processing
                                                        some are intended to be rendered for viewing by a user
                                                        composite media types can be used to enclose multiple representations in a single message
                                                        rendering ability can be impacted by the choice of content
                                                    mechanism
                                                        elements
                                                            components
                                                                data
                                                                resource metadata
                                                    example instances
                                                        HTML document
                                                        JPEG image
                                                        JSON object
                                                    representation metadata
                                                    ^^^^^^^^^^^^^^^^^^^^^^^
                                                        role
                                                            describes the data
                                                        form
                                                            name-value pairs
                                                                name
                                                                    functions
                                                                        corresponds to a standard that defines the value's structure and semantics
                                                        example instances
                                                            media type
                                                            last-modified time
                                                control data
                                                ^^^^^^^^^^^^
                                                    definition
                                                        solution for
                                                            problems
                                                    functions
                                                        defines the purpose of a message between components
                                                        parameterizes requests and override the default behavior of some connecting architecutral elements
                                                        override the default chache configuration by marking the interaction
                                                            marks
                                                                cacheable
                                                                non-cacheable
                                                                cacheable for only a limited time
                                                    properties
                                                        is included in the request or response message
                                                    example instances
                                                        action being requested
                                                            ?HTTP request methods
                                                        meaning of a response
                                                            ?HTTP status codes
                                                    usecases
                                                        used to modify cache behavior
                                                ?resource metadata control data
                                                ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
                                                    example instances
                                                        source link
                                                        alternates
                                                        vary if-modified-since
                                                        cache-control
                                        limitations
                                            cause
                                    connectors
                                    ----------
                                        definition
                                            is a reference to architecutral components of distributed hypermedia systems
                                            is an implementation of separation of concerns
                                            is an implementation of generality
                                        solution for
                                            problems
                                        functions
                                            provides a generic interface for accessing and manipulating the value set of a resource
                                                regardless of how the membership function is defined or the type of software that is handling the request
                                            encapsulates the activities of accessing resources and transferring resource representations
                                            presents an abstract interface for component communication
                                        types
                                            client
                                            ^^^^^^
                                            server
                                            ^^^^^^
                                            cache
                                            ^^^^^
                                            resolver
                                            ^^^^^^^^
                                                definition
                                                    an architecutral element that translates resource identifiers into network address information needed to establish an inter-component connection
                                                solution for
                                                    problems
                                                pupose of use
                                                    usecases
                                                functions
                                                    translates partial or complete resource identifiers into the network address information needed to establish an inter-component connection
                                                mechanism
                                                    elements
                                                        roles
                                                properties
                                                    use of one or more intermediate resolvers can improve the longevity of resource references through indirection
                                                configuration
                                                example instances
                                                    bind (DNS lookup library)
                                            tunnel
                                            ^^^^^^
                                                example instances
                                                    SOCKS
                                                    SSL after HTTP CONNECT
                                        properties
                                            enhances simplicity by providing a clean separation of concerns and hiding the underlying implementation of resources and communication mechanisms
                                            the generality of the interface enables substitutability of implementation
                                        mechanism
                                            elements
                                                connector interface
                                                    mechanism
                                                        elements
                                                            in-parameters
                                                                mechanism
                                                                    components
                                                                        request control data
                                                                        resource identifier indicating the target of the request
                                                                        optional representation
                                                            out-parameters
                                                                mechanism
                                                                    components
                                                                        response control data
                                                                        optional resource metadata
                                                                        optional representation
                                                            properties
                                                                can be passed as data streams
                                                    roles
                                        limitations
                                            cause
                                        example instances
                                    components
                                    ----------
                        induced disadvantages
                            degraded efficiency
                                cause
                                    standardization of transferring methods
                                    architecture does not use transferring methods that is most appropriate for the specific application's need
                        examples
                    Layered System
                    ==============
                    Code-On-Demand
                    ==============
        limitations
        examples
        

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
                                    allow filtering capabilities in resource collection API
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

## internal links

* [Network-based-Architectural-Styles](Network-based-Architectural-Styles.md)

## external links

* [Roy Fielding's paper](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)
* [REST API Tutorial by Lokesh Gupta](https://restfulapi.net)
