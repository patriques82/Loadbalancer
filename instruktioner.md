1. Serva statisk fil (denna)

    0. cd app
    1. docker build -t app .
    2. docker run -p 9000:80 app
    3. localhost:9000

2. Nginx som enkel proxy server

    1. docker-compose build
    2. docker-compose up
    3. localhost:80

3. Nginx som lastbalancerare

    1. docker-compose up -d
    2. docker-compose ps
    3. docker-compose exec proxy sh
          $ nslookup app => 1 app
    4. docker-compose down

    5. dockers dns som resolver i proxy.conf (resolver 127.0.0.11;)
    6. docker-compose up -d --scale app=4
    7. docker-compose exec proxy sh
          $ nslookup app => 4 app
          Nginx plockar en av adresserna vid start (Round-robin)
    8. docker-compose down

    9. docker-compose up
    10. localhost:80 (refresha flera gånger) olika appar i loggar

