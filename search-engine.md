search engine
    core functions
        crawl
        index
        search for indexes
    components
        crawler
            web crawler
                I/O
                    input
                        seeds
                            a seed is initial list of URLs to visit
                        crawl frontier
                            is list of URLs to visit
                    output
                        documents downloaded from visited websites
                role
                    while search depth has not been reached:
                        automatically visit and download resources at URLs listed in the seed
                        visit all websites that are hyperlinked to the visited websites and download resources
                crawling policies
                    crawling policy
                        is combination of policies that defines the behavior of a crawler
                            "the behavior of a crawler is an outcome of combination of policies"
                                https://en.wikipedia.org/wiki/Web_crawler#Crawling_policy
                    classification
                        selection policy
                            restricting followed links
                            URL normalization
                            path-ascending crawling
                            focused crawling
                                academic-focused crawling
                                semantic focused crawling
                        re-visist policy
                        politeness policy
                        parallelization policy
                web scraper
                    task
                        makes HTTP GET requests to specified URLs and extracts specified data out of the data in the response
                    key roles
                        data fetching
                            is fetching of data for later processing
                            carried out by web crawler
                        data extraction
                            perform operation on fetched documents
                                parse
                                search
                                reformat
                                store in database
                open source implementations
                    Apache Nutch
        indexer
            I/O
                input
                output
        document index
            inverted index
                is a mapping of contents to its location
                variants
                    record-level inverted index
                        contains a list of references to documents for each word
                    word-level inverted index
                        contains
                            a list of references to documents for each word
                            positions of each word within a document
        parser
            query parser
                I/O
                    input
                    output
        search platform
            I/O
                input
                output
            roles
                maintains full-text index
                handles search queries
                    parses queries
                reorders search results
            search criteria
            ?DBMS functions
            ?implemented search algorithms
            full-text search
            open source implementations
                Apache Solr
        ranker
            I/O
                input
                output
        interface
            I/O
                input
                    user query
                output
                    search result
                        list of URLs
            examples
                HTML form
                HTML document
                
how to build a search engine
    high level
        scrape the web
        create index of the web
        store the created index on a database
        run a ranking algorithm on the index in order to reorder the index in a particular way
        implement a function that takes a set of search queries and try find and retrieve from the database, a set of index records that has a key that matches the search queries.
        transmit the retrieved records to the client
    entity specific perspectives
        Nutch (web crawler)
            install
            configure 
                agent name
                indexing criteria
                scope of the index to create
                    a region of the web
                enable necessary plugins
        seed file
            create
            populate with URLS
        Solr
            configure
                Reranker
