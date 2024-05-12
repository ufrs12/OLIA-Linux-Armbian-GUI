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

### Deploy
```bash
dotnet publish -c Release -o publish -r linux-arm64
```
or
```bash
dotnet publish -c Release -o publish -r linux-x64
```
```bash
sudo nano /etc/systemd/system/kestrel-test.service
```
```
[Unit]
Description=Example .NET Web API Application running on Ubuntu

[Service]
WorkingDirectory=/home/alexey/publish #путь к publish папке вашего приложения
ExecStart=/usr/bin/dotnet /home/alexey/publish/backend.dll # путь к опубликованной dll
Restart=always
RestartSec=10 # Перезапускать сервис через 10 секунд при краше приложения
SyslogIdentifier=dotnet-example
User=root # пользователь, под которым следует запускать ваш сервис
Environment=ASPNETCORE_ENVIRONMENT=Production

[Install]
WantedBy=multi-user.target
```

```bash
sudo systemctl enable kestrel-test.service
sudo systemctl start kestrel-test.service
```


 /etc/nginx/sites-available/webapi.conf  

 ```
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
 ```
 ```bash
sudo ln -s /etc/nginx/sites-available/webapi.conf /etc/nginx/sites-enabled/webapi.conf
 ```

## Frontend

`ng new frontend`
SCSS  
Server-Side Rendering  

`npm install bootstrap`  
`npm install font-awesome`  
In "build"/"styles" add:  
`"node_modules/bootstrap/dist/css/bootstrap.min.css",`  
`"node_modules/font-awesome/css/font-awesome.min.css",`  
              

