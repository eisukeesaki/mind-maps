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
        functionalities
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
                                        functionalities
                                            makes requests via connector to servers that triggers reactions from servers
                                server
                                ^^^^^^
                                    definitions
                                        a reactive and non-terminating process which offers services to clients
                                    roles
                                        functionalities
                                            waits for requests to be made and then reacts to them
                                                operations
                                                    listens for requests upon services
                                                    rejects or performs request and sends response to client
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
                        functionalities
                            enforces clients and servers to make comprehensive requests/responses
                        mechanism
                            elements
                                constraints
                                ^^^^^^^^^^^
                                    each request must contain all of the information necessary to understand the request
                                    a request cannot take advantage of any stored context on the server
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
                        functionalities
                            partially or completely eliminate some interactions
                        mechanism
                            elements
                                requirements
                                    response must indicate cacheability (reusability)
                                        labels
                                            cachable
                                            non-cacheable
                                    roles
                                        allows clients to determine the reusability of and accessibility to the reusable (cacheable) response data
                        induced disadvantages
                            ?decreased reliability
                                mechanism
                                    cause
                                        stale data within the cache differs significantly from the data that would have been obtained had the request been sent directly to the server
                    Uniform Interface
                    =================
                        definition
                            an architectural style for network-based applications
                            ?an architecutral constraint ...
                        solution for
                            problems
                                how to simplify the overall system architecure and improve the visibility of interactions
                                how to encourage independent evolvability of architecutral components
                        functionalities
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
                                        functionalities
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
                                                    functionalities
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
                                                    functionalities
                                                        defines the purpose of a message between components
                                                        parameterizes requests and override the default behavior of some connecting architecutral elements
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
                                        solution for
                                            problems
                                        functionalities
                                            provide a generic interface for accessing and manipulating the value set of a resource
                                                regardless of how the membership function is defined or the type of software that is handling the request
                                        mechanism
                                            elements
                                                    roles
                                        limitations
                                            cause
                                        examples
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
        
        

notes - Roy Fielding's paper - first pass
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
                                        allows
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
            abstraction of the architectural elements
                within a distributed hypermedia system
            a hybrid
                of the three options available for distributed hypermedia architect
                    the options
                        render the data where it is located and send a fixed-format image to the recipient
                        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
                            the Client-Server style
                            advantages
                                allows all information about the true nature of the data to remain hidden within the sender
                                    prevents assumptions from being made about the data structure
                                        makes client implementation easier
                            disadvantages
                                severly restricts the functionality of the recipient
                                places most of the processing load on the sender
                                    can cause scalability problems
                        encapsulate the data with a rendering engine and send both to the recipient
                        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
                            the mobile object style
                            advantages
                                provides information hiding while enabling specialized processing of data
                                    via its unique rendering engine
                            disadvantages
                                limits the functionality of the recipient
                                    to what is anticipated within that engine
                                may vastly increase the amount of data transferred
                        send the raw data to the recipient along with the metadata that describes the data type
                        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
                            so that the recipient can choose their own rendering engine
                                advantages
                                    allows the sender to remain simple and scalable
                                    minimizes the bytes transferred
                                disadvantages
                                    loses the advantage of information hiding
                                    requires that both sender and recipient understands the data types
        REST components
            is
                set of architecutral constraints
                    chosen for the properties they induce
                        on candidate architectures
            do
                communicate by transferring a representation of a resource
                    in a format matching one of an evolving set of standard types
        ignores the details
            of
                component implementation
                protocol syntax
        focuses on
            roles of the components
            the constraints upon their interaction with other components
            their interpretation of significant data elements
            shared understanding of data types
                with metadata
                but limiting the scope of what is revealed to a standardized interface
        encompasses
            fundamental constraints
                upon
                    components
                    connectors
                    data
                        that define the basis of the Web architecture
            essence of its behavior
                as a network-based application
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
                resource
                    solution for
                        problems
                            
                    definition
                        any information that can be named
                        the intended conceptual target of a hypertext reference
                        conceptual mapping to set of entities
                        definition is abstract
                            allows features of the Web architecture
                    functionalities
                        abstracts information
                            contain
                                any concept that might be the target of an author's hypertext reference           
                    mechanism
                        elements
                            roles
                    examples
                        weather information
                        person
                        e-commerce order details
                    necessity
                        because it may be an element of a service
                resource identifer
                    examples
                        URL
                        URN
                representation
                    definition
                        sequence of bytes + representation metadata to describe the bytes
                    do
                    mechanism
                        elements
                            data
                                represents the resource
                            representation metadata
                                describes the data
                                form
                                    name=value pair
                            metadata of representation metadata
                                describes the metadata of data
                            resource metadata
                                describes about the resource that is not specific to the supplied representation
                            control data
                                defines the purpose of a message between components
                                used to parameterize requests and override the default behavior of some connecting elements
                    limitations
                    examples
                        HTML document
                        JPEG image
                        JSON object
                representation metadata
                    media type
                    last-modified time
                resource metadata control data
                    source link
                    alternates
                    vary if-modified-since
                    cache-control
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
