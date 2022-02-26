#### Getting Janus up & running (sorry about the brevity)

```bash
# Build Docker
docker build -t janus -f Dockerfile .
docker image tag janus:latest ghcr.io/<org>/janus:latest
docker image push ghcr.io/<org>/janus:latest

# Login to GitHub & get the image
docker login ghcr.io -u <username> -p <token>
docker login ghcr.io --username <username> --password-stdin
docker pull ghcr.io/<org>/janus:latest

# Run the image as a daemon (on the command line)
# docker container stop -t janus
DOCKER_IP=94.237.81.25 docker run -p 80:80 -p 7088:7088 -p 8088:8088 -p 8188:8188 -p 8089:8089 -p 10000-10200:10000-10200/udp -d ghcr.io/<org>/janus
```