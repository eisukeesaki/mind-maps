# Amazon Web Services

```text

Amazon Web Services (AWS)
    Elastic Cloud 2 (EC2)
        computational resources
        UI tools
            awscli
            aws-shell
        how to start instance
            signup
            key pair
                create
                    public key encryption
                    used to secure login information
                configure access permission of private key
                    read access to only myself
                        chmod 400
                create security group
                    configure
                        rules
                            inbound
                            outbound
                instance
                    launch
                        on Elastic Block Store
                    connect
                    cleanup
        availability zones
            is
                isolated data center
                specifiable
            Elastic Block Storage
                security group
                    virtual firewall
                    instance
                        internet
                            admin terminal
                                private key
                    AWS managemnt console
                    AWS account
                        IAM administrator
                            single-sign-in identity
                                  └─ authentication scheme
                                         allows user to login with single identity
                                             to several related
                                                 yet independent software systems
                            root user
                                can create
                                    IAM identities
                                        IAM user group
                                            collection
                                                IAM users
                                                    IAM user
                                                        represents
                                                            user of AWS account
                                                        provides
                                                            access to AWS account
                                                        can be
                                                            authenticated
                                                                credentials
                                                                    name
                                                                    password
                                                            authorized to perform actions in AWS
                                        IAM roles
                                            has set permission policies
                                            reusable on multiple IAM users
                                                not uniquely associated with one person
                                            does not have credentials
                                    permission policies
                                        determine
                                            who
                                                user
                                                role
                                                member of a user group                
                                            properties of priviledges
                                                what actions
                                                which AWS resource
                                                what conditions
                  Billing Console
                      create budget
                          wait for AWS Cost Management to become available
    Virtual Private Cloud (VPC)
        ? environment to launch AWS services
    RDS over EC2
        Relational Database Service (RDS)
            managed database service
                functions
                    handles
                        relational database
                            configuration
                                set up
                            administration
                                operate
                                scale
                                other management tasks
                    features
                        backups
                        patching
                        automatic failure detection
                        recovery
                        high availability
                        access management
                            AWS identity
                                AWS Access Management
                Aurora
                    fully-managed relational database engine
                        compatibility
                            MySQL
                            PostgreSQL
                        features
                            high performance storage subsystem
                                high throughput
                                    distributed storage
                                        storage
                                            grows automatically as needed
                            automate & standaridize
                                clustering
                                replication
                        uses RDS features for
                            configuration
                            administration
                        handles
                          routine tasks
                              tasks
                                  ?provisioning
                                  patching
                                  backup
                                  failure recovery
                                  failure detection
                                  repair
                              interface
                                  RDS AWS Management Console                               
                                  CLI commands
                                  API operations


```

