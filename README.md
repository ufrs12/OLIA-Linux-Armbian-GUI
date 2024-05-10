# OLIA-Linux-Armbian-GUI

## Backend
```bash
dotnet new webapi -n backend

```
```bash
cd ./backend

```

```bash
dotnet run

```
Add .gitignore from here. 

In browser(port see in terminal):  

`http://localhost:5111/weatherforecast`  

 /etc/nginx/sites-available/aspnetcore.conf  

 `
 server {
    listen 8888; # указываем порт, по которому nginx будет слушать запросы  
    location / {  
        proxy_pass http://localhost:5000; # указываем порт нашего приложения  
        proxy_http_version 1.1;  
        proxy_set_header Upgrade $http_upgrade;  
        proxy_set_header Connection keep-alive;  
        proxy_set_header Host $host;  
        proxy_cache_bypass $http_upgrade;  
    }  
}  
 `

## Frontend

`ng new frontend`
SCSS  
Server-Side Rendering  
