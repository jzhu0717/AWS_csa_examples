# Create serverless cache

```sh
aws elasticache create-serverless-cache --serverless-cache-name my-cache-jz0717 --engine redis --major-engine-version 7
```

# Install Redis Client (Ubuntu)

```sh
curl -fsSL https://packages.redis.io/gpg | sudo gpg --dearmor -o /usr/share/keyrings/redis-archive-keyring.gpg
sudo chmod 644 /usr/share/keyrings/redis-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/redis-archive-keyring.gpg] https://packages.redis.io/deb $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/redis.list
sudo apt-get update
sudo apt-get install redis
```

# Connect to instance

```sh
redis-cli -h my-cache-jz0717-930c2z.serverless.use1.cache.amazonaws.com:6379
```
