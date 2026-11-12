## Module 1 — Redis Fundamentals
High priority
 2 hours

Topics
- What Redis is and when to use it
- Redis vs PostgreSQL vs MongoDB
- In-memory architecture and why Redis is fast
- Redis event loop and command execution
- Redis as a cache, database, message broker, and coordination tool
- Installing Redis with Docker
- Redis CLI and Redis Insight
- Basic commands: SET, GET, DEL, EXISTS, EXPIRE, TTL, INCR, MGET, MSET
### Interview questions
1. Why is Redis fast despite primarily executing commands on a single thread?
2. Can Redis replace PostgreSQL?
3. Is Redis always faster than a traditional database?
4. What happens when Redis runs out of memory?
Hands-on: Start Redis using Docker, connect through the CLI, store values, set expiry, and inspect keys.
## Module 2 — Redis Data Structures
High priority
 2–3 hours
- Data structure	Practical use case
- Strings	Cache, counters, tokens
- Hashes	User profiles, shopping carts
- Lists	Simple queues, recent activity
- Sets	Unique users, membership
- Sorted Sets	Leaderboards, ranking
- Streams	Event processing, work queues
- Bitmaps	Daily activity tracking
- HyperLogLog	Approximate unique-user counts
- Geospatial	Nearby drivers, stores

Also cover JSON documents where RedisJSON is available, and the time/space complexity of commonly used operations.

### Interview questions
1. How would you build a real-time leaderboard?
2. How would you count daily unique active users?
3. How would you find drivers near a customer's location?
4. When would you use a Sorted Set instead of a regular Set?
Hands-on: Build a leaderboard with scores and rankings using Sorted Sets.
## Module 3 — Caching Strategies
Critical for interviews
 3 hours

Topics
- Cache-aside / lazy loading
- Read-through and write-through
- Write-behind / write-back
- Cache invalidation and cache consistency
- TTL and expiration strategies
- Eviction policies: LRU, LFU, random, TTL-based
- Cache penetration, cache breakdown, cache stampede
- Thundering herd problem
- Negative caching
- Cache warming and prefetching
- Cache key design and versioning
Cache-aside pattern
On a cache hit, FastAPI returns the cached value. On a miss, it reads PostgreSQL and populates Redis.
### Interview questions
1. How do you prevent cache stampedes?
2. How do you keep Redis and PostgreSQL consistent?
3. What happens if Redis goes down?
4. How would you cache a product catalog with millions of products?
Hands-on: Implement cache-aside in FastAPI with Redis and PostgreSQL.
## Module 4 — Redis with Python and FastAPI
High priority
 3 hours

Topics
- redis-py and redis.asyncio
- Redis connection pooling
- Async vs synchronous Redis operations
- FastAPI lifespan and dependency injection
- Caching API responses
- Redis-backed user sessions
- Distributed rate limiting
- Sliding-window and token-bucket algorithms
- Idempotency keys for APIs
- Handling Redis timeouts and connection failures
### Interview questions
1. How would you implement 100 requests/minute per user?
2. How do you prevent duplicate payment processing?
3. Why use async Redis clients in FastAPI?
4. What happens when Redis connection limits are exhausted?
Hands-on: Implement a rate limiter for FastAPI.
## Module 5 — Redis Messaging and Background Processing
2 hours

Topics
- Redis Pub/Sub
- Redis Streams
- Consumer groups
- Message acknowledgment
- Pending entries and recovery
- At-most-once vs at-least-once delivery
- Redis-based background jobs
- Celery with Redis as a broker
- Redis Streams vs Kafka vs RabbitMQ
### Interview questions
1. Why is Redis Pub/Sub unsuitable for durable messaging?
2. How do consumer groups work?
3. What happens if a consumer crashes before acknowledging a message?
4. When would you choose Kafka instead of Redis Streams?
Hands-on: Build a notification-processing worker using Redis Streams.
## Module 6 — Transactions, Atomicity and Distributed Locks
Critical for interviews
 2 hours

Topics
- Atomic Redis commands
- MULTI, EXEC, WATCH
- Optimistic concurrency control
- Lua scripting and Redis Functions
- Race conditions
- Distributed locks with SET NX PX
- Lock expiration and safe release
- Redlock and its limitations
- Fencing tokens
- Why Redis locks alone may be insufficient for correctness-critical operations
### Interview questions
1. How would you prevent two users from booking the same seat?
2. Are Redis transactions equivalent to SQL transactions?
3. How would you implement a distributed lock?
4. What happens when a worker pauses longer than its lock TTL?
Hands-on: Implement an atomic inventory reservation with concurrent requests.
## Module 7 — Persistence, Replication and High Availability
2 hours

Topics
- RDB snapshots
- Append-only file (AOF)
- RDB vs AOF trade-offs
- Restart and recovery
- Primary-replica replication
- Asynchronous replication and replication lag
- Redis Sentinel
- Automatic failover
- Split-brain scenarios
- Data loss during failover
- Durability guarantees and limitations
### Interview questions
1. What happens if the Redis primary crashes?
2. Does replication guarantee zero data loss?
3. How does Sentinel detect failures?
4. Can Redis provide strong consistency?
Hands-on: Configure persistence and test a restart; optionally simulate failover.
## Module 8 — Redis Scaling and Cluster Architecture
Critical for system design
 3 hours

Topics
- Vertical vs horizontal scaling
- Read scaling with replicas
- Write scaling through sharding
- Redis Cluster architecture
- 16,384 hash slots
- Key distribution and hash tags
- Cluster-aware clients
- MOVED and ASK redirects
- Online resharding
- Hot keys and hot shards
- Pipelining and batching
- Network bottlenecks
- Memory fragmentation
- Redis Cluster vs Sentinel
### Interview questions
1. How do you scale Redis writes to 1 million operations per second?
2. Why don't read replicas improve write throughput?
3. What happens when a cluster node fails?
4. How would you identify and resolve a hot key?
5. Why can multi-key operations fail across different hash slots?
Hands-on: Run a local Redis Cluster and observe key distribution.
## Module 9 — Production Monitoring and Security
1–2 hours

Topics
- INFO, SLOWLOG, LATENCY, MEMORY USAGE
- Cache hit ratio
- Evictions and expired keys
- Connection and memory monitoring
- maxmemory configuration
- Identifying expensive commands
- Avoiding KEYS on large production datasets
- ACLs, authentication, TLS, network isolation
- Redis observability with Prometheus and Grafana
- Benchmarking with redis-benchmark
### Interview questions
1. Redis latency suddenly increases. How would you debug it?
2. Why can Redis memory usage exceed the size of stored data?
3. How do you diagnose a falling cache hit ratio?
Hands-on: Benchmark Redis and investigate slow commands.
## Module 10 — Advanced Redis and AI Applications
Optional · 1–2 hours
- Redis vector search and embeddings
- Semantic caching for LLM responses
- Redis as short-lived conversational state
- Redis for retrieval-augmented generation (RAG)
- Redis Bloom filters and probabilistic structures
- Redis vs dedicated vector databases
Redis now supports additional data types and capabilities for vector search and AI workloads. 
Docs+1

Final project — Production-style FastAPI application
Build a Task Management API using FastAPI, PostgreSQL, and Redis, extending your full-stack project.
Feature	Redis concept
Cache task and project details	Cache-aside, TTL
API request throttling	Rate limiting
User login sessions	Session storage
Background notifications	Redis Streams
Prevent duplicate operations	Idempotency
Concurrent task updates	Atomic operations
Activity leaderboard	Sorted Sets
Scale application traffic	Redis Cluster

The final exercise should include concurrent requests, simulated Redis failures, latency measurements, and recovery behavior.
