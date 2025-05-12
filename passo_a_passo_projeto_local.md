### Configurações de Ambiente
Baixar imagens docker

	- docker pull thisthiago/jupyter:latest
	- docker pull minio/minio

Criar a rede

	- docker network create lab-02-network

Executar container

	- docker run -d --network lab-02-network --name jupyter  -p 8888:8888 thisthiago/jupyter:latest
	
    - docker run -d --network lab-02-network --name minio -p 9000:9000 -p 9001:9001 -v /home/thiago/work/minio/data:/data -e "MINIO_ROOT_USER=admin" -e "MINIO_ROOT_PASSWORD=senhasegura" quay.io/minio/minio server /data --console-address ":9001"
	
### Configurações para AWS S3 (leitura)
```python
s3_options = {
    "fs.s3a.access.key": "",
    "fs.s3a.secret.key": "",
    "fs.s3a.endpoint": "s3.us-east-2.amazonaws.com",
    "fs.s3a.region": "us-east-2",
    "fs.s3a.path.style.access": "false"
}
```

### Configurações para MinIO (escrita como Delta)
```python
minio_delta_options = {
    "fs.s3a.access.key": "",
    "fs.s3a.secret.key": "",
    "fs.s3a.endpoint": "http://minio:9000",
    "fs.s3a.path.style.access": "true",
    "fs.s3a.connection.ssl.enabled": "false"
}
```