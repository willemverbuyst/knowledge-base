__`docker-compose.yml`__
```yml
version: '3'
services:
  mongodb:
    image: mongo
    container_name: kb-mongodb
    ports:
      - 27017:27017
    env_file:
      - ./.env
    volumes:
      - mongo-db:/data/db
    networks:
      - kb-net
  mongodb-seed:
    build:
      context: ./data
      dockerfile: Dockerfile
    depends_on:
      - mongodb
    container_name: kb-mongodb-seed
    networks:
      - kb-net
networks:
  kb-net:
    driver: bridge

volumes:
  mongo-db:
```

__`.env`__
```TXT
MONGO_INITDB_DATABASE=\<name of database\>
```

Docker file for mongodb seed

__`data/Dockerfile`__
```yml
FROM mongo

COPY <something>.json /<something>.json

CMD mongoimport --uri mongodb://mongodb:27017/<name of database> --collection <something> --drop --file /<something>.json --jsonArray
```

In the same data folder there should be a json file with the seed data