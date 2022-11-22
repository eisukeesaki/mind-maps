User Interface (UI)
    UI programming
        web application interfaces (web APIs)
            specifications
                Document Object Model (DOM)
            interfaces
                document
                    methods
                        getElementById(id)
                            returns an Element object matching id
        design pattern
            data binding
                definition
                    technique that binds data sources from the provider and consumer together and synchronizes them
                UI data binding
                    functions
                        binds UI elements to an application domain model
                            domain model
                                definition
                                    conceptual model of the domain that incorporates both behavior and data
                    UI data binding libraries
                        definition
                            helper library that allows binding of UI components in layouts to data sources using a declarative paradigm
                        example instances
                            React Redux
        tools
            libraries
                React
                    definition
                        JS library for building UIs
                    use cases
                        implement logical, reusable parts of UI
                    programming paradigm
                        declarative
                            express logic of a computation without describing control flow
                    constituents
                        builtin packages
                            react-dom
                                provides DOM specific methods
                        concepts
                            components
                                classification
                                    class based components
                                    function based components
                                        hooking
                                            definition
                                                range of techniques used to [alter, augment] the behaviour of software components
                                            mechanism
                                                intercepts [function calls, messages, events] passed between software components
                                            use purposes
                                                debugging
                                                extending functionality
                                                rootKits
                                            example instances
                                                keyboard remapping programs
                                                frame rate measuring programs
                                                ?logging programs
                                            hooks
                                                definition
                                                    code that handles intercepted [function calls, messages, events]
                                input
                                    properties (props)
                                output
                                    React element
                        React element
                            definition
                                description of what to render
                            form
                                return value of React.createElement(component, props, ...children)
                        (JSX)
                            definition
                                syntax extension to React.createElement(component, props, ...children)
                            constituents
                                HTML
                                JavaScript
                            properties
                                can embedd JavaScript expressions inside {}
                                is compiled into React.createElement() calls by Babel and evaluated to JavaScript objects
                    ?component lifecycles
                        mounting
                        updating
                        unmounting
                        error handling

