Yii 2 Docker Enviroment(with php_rdkafka && redis-server 3.0.*)
===============================

1. Clone/Upload

       For install advanced Yii2 application edit docker-compose.yml
           - ./docker/nginx/conf.d:/etc/nginx/conf.d # - advanced
           #- ./docker/nginx/conf.dbasic:/etc/nginx/conf.d # - basic
       
       For install basic Yii2 application edit docker-compose.yml
           #- ./docker/nginx/conf.d:/etc/nginx/conf.d # - advanced
           - ./docker/nginx/conf.dbasic:/etc/nginx/conf.d # - basic   
               
2. Run #docker-compose up -d and wait until the deploy is complete
       
       Params for connect to service
       
       Mysql:
           host:        172.18.33.2
           port:        3306
           user:        root
           password:    12345
       
       Redis:
           host:        172.18.33.3
           port:        6379
           password:    123456
           database:    from 1 to 16

3. Enter in php container 
        
        docker exec -it [container-name] bash

4. For install advanced Yii2 application run in container 
    
        composer create-project --prefer-dist yiisoft/yii2-app-advanced ./
        
        php init
        
   For install basic Yii2 application run in container 
   
       composer create-project --prefer-dist yiisoft/yii2-app-basic ./

5. Wait until the composer finishes

6. Configure Yii2 application and run
      
       php yii migrate/up

7. The application is available at 

       http://mysite.local
