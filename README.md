# Docker AutoSSL
A docker file to create the files in a docker env with the objective to share these certs between containers

What you need to configure in the commands below:
- DOMAINS
- EMAIL
- YOUR_SHARED_VOLUME

Use the YOUR_SHARED_VOLUME to get the .pem and .cert from this container!

```
# Build the docker file
docker build \
  --tag autossl:latest \
  .

# Start the docker
docker run -d \
  --name autossl \
  --restart unless-stopped \
  --publish 80:80 \
  --env DOMAINS=www.yourdomain.com \
  --env EMAIL=your@email.com \
  --volume YOUR_SHARED_VOLUME:/etc/autossl \
  autossl:latest
```
