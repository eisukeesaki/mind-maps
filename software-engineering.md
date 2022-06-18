# 

```text

software engineering
    principles
        └─ foundation for system
        separation of concerns
            recognition of the need for human beings to work within limited context
                the human mind is limited to dealing with a limited amount of data at a time
                    7 units of data at a time
                        G.A. Miller
            specializations
                modularity
                    separation of software into components
                        according to
                            functionality
                            responsibility
                abstration
                    separation of the behavior of software components
                        from their implementation
                    requires ability to look at software and software components from two points of view
                        behavior
                            what it does
                        implementaion
                            how it does
                                 what it does
                     failure to follow cause unnecessary coupling
                        example
                            it is common for recursive algorithms to introduce extra parameters to make the recursion work
        anticipation of change
            learning process
                developers
                    learn
                        domain that the end-users work in
                        values of end-users
                            what form of data presentation is most useful to end-users?
                            what kind of data are
                                crucial?
                                require protective measures?
                end-users
                    learn
                        see range of possible solutions that software technology can provide
                        evaluate possible solutions in regards to their effectiveness in meeting the end-users' needs
                prliminary requirements need to be worked out early, but it should be possible to make changes in the requiremenst as learning progresses
                    coupling is a major obstacle to change
                    cohesive components are easy to reuse when requirements change
        generality
            design of software that is free from unnatural restrictions and limitations
                example
                    year 2000 problem
        incremental development
            build software in small increments
                one use case at a time
            simplifies verification
                if there are any errors detected, they are already partly isolated 
                    easier to correct
            carefully planned incremental development process can ease the handling of changes in requirements
                planning must identify use cases that are moset likely to be changed and put them towards the end of the development process
        consistency
            recognition of the fact that it is easier to do things in a familiar context
                examples
                    coding style
                        purposes
                            increases readability
                            allows programmers to automate part of the skills required in code entry
                                frees programmers' mind
            development of idioms for dealing with common programming problems
            in GUI development
                purposes
                    makes learing easier for end-users
                    increases reusability of UI components
            in development of object oriented class libraries
                increases intuitiveness to users

```

```text

How I build computer programs:
    1. identify the main issue that I want to solve
    2. define minimum viable solution for the main issue
    3. recursively break down the main issue into smaller, more specific sub-issues until I know the exact code-level solution for a particular issue
    4. code
        code a little, test a little, repeat
            sizeof "little" will incrementally become larger as my skill develops
    5. reassess issues
    6. repeat

```

## external links

- [Principles of Software Engineering](https://www.d.umn.edu/~gshute/softeng/principles.html)

