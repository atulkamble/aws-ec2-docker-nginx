# 🚀 Docker on Amazon Linux EC2 (t3.micro)

## 1. Launch EC2

* AMI: **Amazon Linux**
* Instance type: **t3.micro**
* Security Group (SG): Allow inbound on ports `22` (SSH), `80`, `1000`, `2000`.
* Key Pair: `docker.pem`

SSH into the instance:

```bash
chmod 400 docker.pem
ssh -i docker.pem ec2-user@<EC2-PUBLIC-IP>
```

---

## 2. Install Docker

```bash
sudo yum update -y
sudo yum install docker -y
docker --version
```

Enable and start Docker:

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

---

## 3. Docker Hub Login

```bash
sudo docker login
```

---

## 4. Run Nginx Containers

Pull image:

```bash
sudo docker pull nginx
sudo docker images
```

Run containers on multiple ports:

```bash
sudo docker run -d -p 80:80 nginx
sudo docker run -d -p 1000:80 nginx
sudo docker run -d -p 2000:80 nginx
```

Check running containers:

```bash
sudo docker container ls
```

---

## 5. Access in Browser

* [http://18.209.20.71](http://18.209.20.71)
* [http://18.209.20.71:1000](http://18.209.20.71:1000)
* [http://18.209.20.71:2000](http://18.209.20.71:2000)

---

## 6. Manage Containers

Stop container:

```bash
sudo docker container stop <container_id>
```

Start container:

```bash
sudo docker container start <container_id>
```

Remove container:

```bash
sudo docker container rm <container_id>
```

List again:

```bash
sudo docker container ls
```

---

## 7. Manage Images

List images:

```bash
sudo docker images
```

Remove image:

```bash
sudo docker rmi nginx
```

Force remove if container still running:

```bash
sudo docker container stop <container_id>
sudo docker rmi nginx -f
```

---

✅ You now have **Docker running with multiple Nginx containers** on Amazon Linux EC2 with exposed ports 80, 1000, and 2000.

