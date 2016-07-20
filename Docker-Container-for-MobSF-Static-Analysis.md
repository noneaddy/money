**Building Image from Dockerfile**

Dockefile is available here: https://github.com/ajinabraham/Mobile-Security-Framework-MobSF/blob/master/Dockerfile

```

docker build -t mobsf_docker .
docker run -i -t opensecurity/mobsf:latest

```

This will run MobSF at 0.0.0.0:8000

**Prebuilt MobSF Docker Image**

https://hub.docker.com/r/opensecurity/mobsf/
```
docker pull opensecurity/mobsf
```