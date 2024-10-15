# Etape1

mkdir etape1 etape2 etape3 etape4

cd ../etape1

mkdir http script config src

echo "<?php phpinfo(); ?>" > src/index.php

docker network create tp2-network

docker build -t http-image -f http/Dockerfile .
docker build -t script-image -f script/Dockerfile .

docker run -d --name script --network tp2-network script-image
docker run -d -p 8080:8080 --name http --network tp2-network http-image