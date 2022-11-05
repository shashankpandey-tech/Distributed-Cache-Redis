# Distributed-Cache-Redis
Redis Cache

Setup .Net Core Application (3.1) -

Package :
Microsoft.Extensions.Caching.StackExchangeRedis
Microsoft.Extensions.Caching.Distributed;

services.AddStackExchangeRedisCache(options =>
{
options.Configuration = Configuration.GetSection("RedisConnection").GetValue<string>("Configuration");
options.InstanceName = Configuration.GetSection("RedisConnection").GetValue<string>("InstanceName");
});

"RedisConnection": {
//Azure Redis Connection String
//"Configuration": "redistest9090.redis.cache.windows.net:6380,password=sYesGg7wc6QQU76T8BFGLQi4vOGji2ZVMAzCaM5u2oM=,ssl=True,abortConnect=False",
// Local redis server runing on current machine
"InstanceName": "RedisInstance_" // Cache key prefix
}

# Note : this will work for both windows redis server and Azure Redis Cache only need to change connection string.
  
Use this interface to access methods - private readonly IDistributedCache _distributedCache;
https://learn.microsoft.com/en-us/aspnet/core/performance/caching/distributed?view=aspnetcore-6.0
  
# Access all distributed cache methods (get/post/remove) by using this interface IDistributedCache.
    
Download zip file from below link, extract and run "redis-server.exe". default post is 6379.
Redis Server Window Setup: https://github.com/microsoftarchive/redis/releases/tag/win-3.0.504
Redis GUI : https://redis.com/redis-enterprise/redis-insight/

For Azure Redis Pricing - https://azure.microsoft.com/en-in/pricing/details/cache/

  # More Info 
  
What is Caching?
What are the use cases of Caching?
How to implement Caching?
Redis is an open source, in-memory data structure store, used as a database, cache, and message broker. Redis provides data structures such as strings, hashes, lists, sets, sorted sets with range queries, bitmaps, hyperloglogs, geospatial indexes, and streams. Redis has built-in replication, Lua scripting, LRU eviction, transactions, and different levels of on-disk persistence, and provides high availability via Redis Sentinel and automatic partitioning with Redis Cluster.

What is Distributed Caching? A cache is a component that stores data so future requests for that data can be served faster. This provides high throughput and low-latency access to commonly used application data, by storing the data in memory. By avoiding the high latency data access of a persistent data store, caching can dramatically improve application responsiveness, if it's well used.

What are the benefits?

Sharing state between different Servers, Applications, Modules or even components that can be in the same or in different infrastructures.
Continuous querying for the same data inside Actions, Screens and Web Services especially when the data changes frequently as in a few seconds.
Storing high transient data, for example, data that is created and deleted after a very short period of time.
