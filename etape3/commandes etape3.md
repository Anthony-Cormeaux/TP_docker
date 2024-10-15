# Etape3

cd "C:\Users\antho\OneDrive\Master\M2\S3\DevOps_MLOps\TP2\docker-tp2\etape3\src"


Invoke-WebRequest -Uri "https://wordpress.org/latest.tar.gz" -OutFile "latest.tar.gz"

tar -xzf latest.tar.gz --strip-components=1


docker run -d --name data --network tp2-network ^
  -e MYSQL_ROOT_PASSWORD=rootpass ^
  -e MYSQL_DATABASE=testdb ^
  -e MYSQL_USER=testuser ^
  -e MYSQL_PASSWORD=testpass ^
  -v "%cd%/data:/var/lib/mysql" ^
  mariadb:latest


docker build -t script-image -f script/Dockerfile .
docker run -d --name script --network tp2-network script-image

docker build -t http-image -f http/Dockerfile .
docker run -d -p 8080:8080 --name http --network tp2-network http-image

http://localhost:8080/