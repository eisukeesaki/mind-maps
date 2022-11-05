The Basics
    static type checking
        use of static type checking mechanism allows programmers to identify type errors at compile time, rather than at runtime
    non-exception failures
        behaviors of runtime errors are specified in ECMAScript specification
        the static type system intends to catch a few types of errors such as typos, uncalled functions, and basic logic errors
    emitting with errors
        Why does tsc generate JavaScript, even if the input TypeScript has type errors?
            Because otherwise, the compiler could break a working codebase
