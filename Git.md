# Git

```text

Git
    repository
        non-bare
            default
        bare
            serve as
                authoritative focal point for collaborative development
            available operations
                clone
                push
    hooks
        event driven
            Git checks /hooks for scripts to run
                run scripts
                    before command
                        to
                            ensure code compliance to standards
                            setup environment
                    after command
                        to
                            deploy code
        category
            client-side hooks
                executed on
                    committer's computer
                trigger
                    committing
                    merging
            server-side hooks
                sub-category
                    pre-receive
                    post-receive
                executed on
                    servers that are used to receive pushes
                trigger
                    receiving of pushed commits
        common use cases
            enforce policies
            ensure consistency
            control environment
            handle deployment tasks
        

```

