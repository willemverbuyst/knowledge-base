```yml
version: '3.8'
services:
  dev-db:
    image: postgres:latest
    ports:
      - 5432:5432
    restart: always
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: password
      POSTGRES_DB: mydb
    networks:
      - mynetwork
networks:
  mynetwork:
```

in dotenv:
`DATABASE_URL=postgresql://<USER>:<PASSWORD>@<HOST>:<PORT>/<DATABASE>?schema=<SCHEMA>`

`DATABASE_URL=postgresql://postgres:password@localhost:5432/mydb?schema=public`
