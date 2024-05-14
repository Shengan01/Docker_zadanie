Aby uruchomic kontener pobierajac obraz zdalnie z repo wystarczy uzyc komendy
```
sudo docker run -d -p 8080:8080 shengan/zadanie:zadanie_final_v2
```
Polecenia uzyte do zbudowania kontenera:
```
export DOCKER_CLI_EXPERIMENTAL=enabled
sudo docker run --rm --privileged docker/binfmt:66f9012c56a8316f9244ffd762267c21c1f6f28d
sudo docker buildx create --driver docker-container --use --name zadanie_builder --bootstrap
sudo docker buildx build docker.io/shengan/zadanie:zadanie_final_v2 --platform linux/amd64,linux/arm64 --cache-from=type=registry,ref=shengan/zadanie:cache --cache-to=type=registry,ref=shengan/zadanie:cache,mode=max --push .
```
Polecenia uzyte do zbudowania kontenera lokalnie:
```
sudo docker build --no-cache -t lightweight_server_c .
```
Polecenia uzyte do uruchomienia kontenera zbudowanego lokalnie:
```
sudo docker run -d -p 8080:8080 --name my_server_c lightweight_server_c
```
Polecenia uzyte do uzyskania informacji z kontenera:
```
sudo docker logs my_server_c
```
Logi serwera:
 ![screen_zadanie_1](https://github.com/Shengan01/Docker_zadanie/assets/142215518/cbc2591f-5a47-48c7-b17d-e6c79234a7ba)

Widok w przegladarce pod adresem http://localhost:8080
![screen_zadanie_2](https://github.com/Shengan01/Docker_zadanie/assets/142215518/0b9eed0f-7129-4ea8-b011-89e6cfb7ae50)

Multiplatformowość, brak podatności  obrazu:
![image](https://github.com/Shengan01/Docker_zadanie/assets/142215518/7f0ed210-ea0e-4029-99e1-126380c07bcb)

Plik cache:
![image](https://github.com/Shengan01/Docker_zadanie/assets/142215518/1da8e314-b7a6-4aee-9f0c-b0f672f5b97f)
