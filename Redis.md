# Redis

## Documentations
- [community Documentation](https://redis.io/docs/)

```text

Redis
    what
        in-memory data structure store
            supported data structures
                keys
                strings
                hashes
                lists
                sets
                sorted sets with range queries
                bitmaps
                hyperloglogs
                geospatial indexes
                streams
        key-value store that can store complex data structures
    featurs
        atomic transaction
            atomicity
                one of the ACID transaction properties
                all occurs or nothing occurs
            example
                INCR(ement) command is atomic
                    it will never happen that client-a reads 10, client-b also reads 10, and the final value become 11. final value will always be 12
        key expiration
        insecure defaults
            binds to all network interface
            has no authentication
            when using for production do
                firewall the port the Redis server listens to
                specify network interface to only listen to
                setup authentication
                    require clients to run AUTH command
                use SSL tunneling to encrypt traffic between servers and clients
                    spiped
                ?install Redis in Linux box using init script
        configuration file
            redis.conf
    use case
        database
        cache
        ?message broker
        ?streaming engine
    actors
        server
        client
            redis/node-redis
            client libraries
                implements Redis specific communication protocols
            communicates with Redis using
                TCP socket
                Redis specific protocols
                    implemented by client libraries
        libraries
            qishibo/AnotherRedisDesktopManager
                    
        tools
            CLI
                redis/redis
            GUI
            Proxy
        modules
            RediSearch/RediSearch
            RedisJSON/RedisJSON
        ?
            Redis stack
            Redis Sentinel
            Redis Cluster

```

