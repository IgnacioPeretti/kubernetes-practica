## Como crear una imagen multi arquitectura con Docker Buildx

### Crear un archivo Dockerfile

```Dockerfile
FROM alpine:3.12
RUN apk add --no-cache curl
CMD ["curl", "https://www.google.com"]
```

### Crear una imagen multi arquitectura

```bash
docker buildx create --use
docker buildx build --platform linux/amd64,linux/arm64 -t multi-arch:latest --push .
```

### Verificar las arquitecturas soportadas

```bash
docker buildx inspect --bootstrap
```

### Correr la imagen en un contenedor

```bash
docker run -p 80:80 registry/image:tag
```

### Validar que esta corriendo
    
```bash
curl -i http://localhost
```

### Crear nuestro primer pod en minikube

```bash
kubctl apply -f pod-1.yaml
```

### revisar si esta funcionando

```bash
kubectl get pod -n clase43
```


