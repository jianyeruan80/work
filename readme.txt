1,docker run -d --name data -v $PWD/app:/usr/share/jayruanwork centos
2,docker run -d --name=nginx -p 80:80 --volumes-from=data -v $PWD/config/nginx:/etc/nginx/conf.d nginx
3,docker run -d --volumes-from=data --name mongo -p 27017:27017 mongo
4,docker run -d --volumes-from=data --name=nodejs -p 3001:3001 jianyeruan/node supervisor vip/app.js