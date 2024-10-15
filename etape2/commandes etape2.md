# Etape2

création du dossier étape 2 et recopie des ressources de l'étape 1 ...

cp -r ../etape1/* .

mkdir data

docker run -d --name data --network tp2-network ^
  -e MYSQL_ROOT_PASSWORD=rootpass ^
  -e MYSQL_DATABASE=testdb ^
  -e MYSQL_USER=testuser ^
  -e MYSQL_PASSWORD=testpass ^
  -v "%cd%\data\sql:/docker-entrypoint-initdb.d" ^
  mariadb:latest

reconstruction de l'image et du container
docker stop script
docker stop script

docker build -t script-image -f script/Dockerfile .
docker run -d --name script --network tp2-network script-image

docker stop http
docker rm http

docker build -t http-image -f http/Dockerfile .
docker run -d -p 8080:8080 --name http --network tp2-network http-image

tester dans le navigateur : http://localhost:8080/test_bdd.php