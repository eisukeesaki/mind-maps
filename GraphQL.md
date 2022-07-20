# GraphQL

```text

GraphQL
    Schema Definition Language (SDL)
        is a type system
        can specify data relationships
        can be used to define schema of API
    GraphQL Schema
        syntactic entities
            root type
                defines type of operation
                    Query
                        is
                            request for read operation
                            detailed information about the data being requested
                        relevant entities
                            root field
                            payload
                    Muration
                        request for write operation 
                            create
                            update
                            delete
                    Subscription
                        request for real-time data
                        function
                            real-time communication
                                event-driven
            root field
                entry point to GraphQL server
                defines structure of response fields based on the object fields selected
      GraphQL clients
          Apollo
          Relay
      How to add feature to API
          schema driven/first development
              1. extend schema definition
              2. implement corresponding resolver functions

GraphQL-notes
    declarative data retrieval
    single API endpoint handles all requests
    abstracts away from application developers
        endpoints
        HTTP methods
        status codes
    problem that it solves
        REST N + 1 problem
            is
                Client application underfetches or overfetches data.
            solution to itself creates different problem
                Coupling of client application and API.
                    cause
                        Because of the mismatch between the data structure that
                            APIs returns
                            client app requires,
                            either
                                API
                                client 
                            must adapt to either
                                API
                                client.
                            To adapt is to couple.
        API documentation problem
            lack of/outdated documentation
                caused by
                    cost to create and maintain
                    REST doesn't force developers to create documentation.
            solved by
                GraphQL Schema
                    type system
        poor API usage tracking
            REST tracks API usage through frequency of calls
                with GraphQL, it's possible to track calls through the forms(data being asked for) of the calls 

```

## resources
- [QraphQL - Core Concepts](https://www.howtographql.com/basics/2-core-concepts/)
- 
