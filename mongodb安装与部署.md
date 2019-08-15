1. 查看服务器是否安装mongo
   
    rpm -qa|grep mongo
    
2. 添加mongodb的yum源以mongo 3.4为例。
   cd /etc/yum.repos.d/

   vim mongodb-3.4.repo
   
   [mongodb-org-3.4]

   name=MongoDB Repository
   
   baseurl=https://repo.mongodb.org/yum/redhat/$releasever/mongodb-org/3.4/x86_64/
  
   gpgcheck=1
   
   enabled=1
   
   gpgkey=https://www.mongodb.org/static/pgp/server-3.2.asc
   
   
   这里可以修改 gpgcheck=0, 省去gpg验证 
  
3. 安装mongo

   yum install -y mongodb-org
   
4. 查看mongo 的版本 
   
   mongo --version
   
5. 启动,关闭 mongo
   
   systemctl stop mongod
   
   systemctl start mongod
   
 6. 密码认证
 
    shell>mongo
    
    use admin 
    
    db.createUser({user:"admin",pwd:"123456",roles:["root"]}) 
    
    db.auth("admin", "123456")
 
7.启用密码登录（需要配置文件 /etc/mongod.conf ）
 
   security:
      
      authorization: enabled
      
    systemctl restart mongod
    
8.密码认证登录 

   mongo --port 27017 -u 'admin' -p '123456' --authenticationDatabase 'admin'
   
   创建普通用户 
   
   use voice
   
   db.createUser({user: "voice", pwd: "iKDpwGmQuRlWgzAJ", roles: [{ role: "dbOwner", db: "voice" }]})
   
   
   show users
   
   
   
    
    
