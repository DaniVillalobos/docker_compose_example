vote 
    docker build . -t voting-app
    docker run -p 5000:80 voting-app

redis
    docker run -d --name=redis redis

docker run -p 5000:80 --link redis:redis voting-app

db
    docker run -d --name=db -e POSTGRESS_PASSWORD=password postgres:9.4

worker 
    docker build . -t worker-app
    docker run --link redis:redis --link db:db worker-app

result
    docker build . -t result-app
    docker run -p 5001:80 --link db:db result-app