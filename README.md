### Dockerized nginx for routing
No ssl yet

#### Deploy

    cdc icu
    dc build
    dc up -d

  This should do the trick  🪄



####
 ```
    certbot certonly --manual --preferred-challenges=dns -d '*.tldr.icu'
    dig @8.8.8.8 tldr.icu TXT
 ```