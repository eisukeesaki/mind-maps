# Git

```text

Git
    actors
        project root directory
            contains Git repository
        Git repository
             tracked files + .git
        commit
            records snapshot of all tracked files in repository
            has meta information
                date created
                reference to its ancestor
                    a ancestor
                        is a commit that a descendant commit was based off of
                enables Git to record history of commits
        branch
            pointer that points to a commit
        HEAD
            a pointer that points to a commit
        delta
            set of changes made to tracked files
    states
        to be on a branch
            HEAD is pointing to a branch
    commands
        moving around inside repository
            checkout
                instructs Git to point HEAD to a given argument
                    arguments
                        branch
                        commit
        combine work
            merge
                create new commit that
                    points to two ancestors
                    virtually contains entire histroy of two branches
            rebase
                create a copy of HEAD
            pull
                fetch + merge
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

