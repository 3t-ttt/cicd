# deploy FE
1. folder, user

  mkdir folder
  mv file.zip folder
  sudo adduser username
  sudo passwd username
  sudo su
  passwd
  
  ls -l
  sudo chown -R user:usergroup folder
  sudo chmod -R 750 folder
  

2. build, run
  install tool for build and run
  su username
  vi package.json
  vi vue.config.js
  npm install
      0. 
        npm run build
        npm run serve
      1. websever: nginx
        exit -> root user
        sudo apt install nginx
        netstat -tlpun
        check port in nginx
             cd /etc/nginx/
             vi sites-available/default
             nginx -t
             systemctl restart nginx
             netstat -tlpun
         vi conf.d/todolist.conf
           server {
               listen 8081;
               root /projects/todolist/dist/;
               index index.html;
               try_files $uri $uri/ /index.html;
           }
         nginx -t
         systemctl restart nginx
         netstat -tlpun
         vi /etc/nginx/nginx.conf -> user www-data
         sudo usermod -aG tintt www-data
         sudo nginx -s reload

      2. service
          npm install
          vi /lib/systemd/system/vision.service
[service]
Type=simple
User=vision
Restart=on-failure
WorkingDirectory=/projects/vision/
ExecStart=npm run start -- --port=3000   

          


      4. pm2



# cicd
