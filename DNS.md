# DNS

```text

Domain Name System (DNS)
    function
        identifies computers on the internet
        eliminats the need for users to remember IP addresses which can change overtime
    architecture
        distributed, decentralized database
    components
        domain name
            what
                human friendly representation of IP addresses
            classification
                fully qualified domain name
                    a.k.a
                        absolute domain name
                    specifies exact location in tree hierarchy of DNS
                        specifies all domain levels
                  partially qualified domain name
                    a.k.a
                        relative domain name
                    does not include all all labels to DNS root
                    can be
                        hostnames
                            left-most lable in a fully qualified domain name
        domain name servers
            definition
                nodes within the distributed database system (DNS)
            role
                implements DNS
            server
                stores resource records
                responds to queries against its database
            function
                translates domain names and hostnames into corresponding IP addresses
        resource records
            roles
                maps domain names and IP addresses
            types
                A
                    Address record
                NS
                    Name Server record
                SOA
                    Start Of Authority
                        holds administrative information
                ...
            syntax
                [name] [type] [class] type data
        domain namespace
            is organized into tree data structure
                components
                    node
                        label
                        resource records
                DNS zone tree
                    constituents
                        forward mapping
                            hostnames to IP addresses
                        reverse mapping
                            IP addresses to hostnames
            domain name hierarchy
            IP address system
        DNS zones
            is
                specific, distinctly managed areas in DNS namespace
                    managed by
                        organization
                        administrator
            strucutre
                root domain (.<empty string>)
                    top-level domain (com)
                        second level domain (google)
                            third level domain (developers)
                                ...
        domain name registry
            database of all domain names and the associated registrant information in the top level domains
    relevant entities
        domain
            area owned by a owner
        domain name registrars   
            companies that manages the reservation of internet domain names
        DNS providers
            Amazon
                AWS Route 53
            Cloudflare

Domain Name System (DNS) (DEPRECATED)
    function
        identifies computers on the internet
        acts as distributed database
        maps domain name and IP address
    properties
        hierarchical
        decentralized
    domain
        area owned by a owner
    DNS service providers
        Amazon
            AWS Route 53
        Cloudflare
    architecture
        domain's server
            roles
                queries other domain's servers about names in their domain
                answers queries from other domain's server about names in its own domain
        example
            siteA
                stores data for computers it knows about
            siteB
                stores data for its own set of computers
    query
        cosists of
            name
            record type
                A record
                    IP address associated with a name
        query response
            resource records (RR)
                associates domain names with IP addresses
                a record
                    [name] [type] [class] type data
                types
                    A
                        Address record
                    NS
                        Name Server record
                    ...
            message indicating that the queried name does not exist
    DNS for lookups
        configuration
            configure systems as clients
                /etc/resolv.conf
                    client-side resolver
                        lists name servers to which the host can send queries to
            when to use DNS as opposed to other name lookup methods?
                                            └─ /etc/hosts
                /etc/nsswitch.conf
                    specifies
                        how hostname-to-IP-address should be performed
                        DNS should be tried first? last? or at all?
    DNS namespace
        zone tree
            forward mapping
                hostnames to IP addresses
            reverse mapping
                IP addresses to hostnames
        example
            URL
                www.developers.google.com
                --- ---------- ------ ---
                 │      │         │    └─ top-level domain
                 │      │         └─ second-level domain
                 │      └─ subdomain
                 └─ subdomain
                ---------------------
                         └─ host
       zone
          domain - subdomains
    name servers
        roles
            answers queries about its own site's hostnames and IP addresses
            queries about both local and remote hosts on behalf of users
            caches resource records
            communicates with other local namer servers to synchronize DNS data
        classification
            authoritative
            primary
            master
            secondary
            slave
            stub
            distribution
            non-authoritateive
            caching
            forwarder
            recursive
            nonrecursive
    DNS database

```

