# Distributed-Cache-Redis
Redis Cache

Setup On Window Machine -

Package :
Microsoft.Extensions.Caching.StackExchangeRedis
Microsoft.Extensions.Caching.Distributed;

services.AddStackExchangeRedisCache(options =>
{
options.Configuration = Configuration.GetSection("RedisConnection").GetValue<string>("Configuration");
options.InstanceName = Configuration.GetSection("RedisConnection").GetValue<string>("InstanceName");
});

"RedisConnection": {
"Configuration": "localhost:6379", // This one is where local redis server runing
"InstanceName": "RedisInstance_" // Cache key prefix
}

Use this interface to access methods - private readonly IDistributedCache _distributedCache;
  https://learn.microsoft.com/en-us/aspnet/core/performance/caching/distributed?view=aspnetcore-6.0
  
Access distributed cache methods by using this interface IDistributedCache.
Download zip file from below link, extract and run "redis-server.exe". default post is 6379.
Redis Server Window Setup: https://github.com/microsoftarchive/redis/releases/tag/win-3.0.504
Redis GUI : https://redis.com/redis-enterprise/redis-insight/

For Azure Redis Pricing - https://azure.microsoft.com/en-in/pricing/details/cache/
