git clone https://github.com/jianyeruan80/work.git
1,docker run -d --name data -v $PWD/app:/usr/share/jayruanwork centos
2,docker run -d --name=nginx -p 80:80 --volumes-from=data -v $PWD/config/nginx:/etc/nginx/conf.d nginx
3,docker run -d --volumes-from=data --name mongo -p 27017:27017 mongo
4,docker run -d --volumes-from=data --name=nodejs -p 3001:3001 jianyeruan/node supervisor vip/app.js

5,docker exec mongo mongodump -d testdb -o /usr/share/jayruanwork/mongo
6,docker exec mongo mongorestore -d testdb /usr/share/jayruanwork/mongo/testdb

mongoexport -d testdb -c students --csv -f state,name,phone -o students_csv.csv
mongoimport -d testdb -c students students.csv 

7,docker run  --name redis -it -p 6379:6379  redis redis-server  --appendonly yes