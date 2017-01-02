<h1>For docker</h1>

<i>- Delete all docker container</i><br/>
docker rm $(docker ps -a -q) -f<br/><br/>

<i>- Delete all docker images</i><br/>
docker rmi $(docker images -q) -f<br/><br/>

<i>- Build images</i><br/>
docker build -t hathanhtamnd/image_name:latest .<br/><br/>

<i>- Docker login</i><br/>
docker login<br/><br/>

<i>- Upload to dockerhub</i><br/>
docker push hathanhtamnd/image_name:latest<br/><br/>

<i>- Pull docker images</i><br/>
docker pull hathanhtamnd/image_name<br/><br/>

<i>- Create network</i><br/>
docker network create --subnet=172.0.0.0/16 dockernetwork<br/><br/>

<i>- Run docker</i><br>
docker run -it --cap-add=SYS_ADMIN -e "container=docker" -v /sys/fs/cgroup:/sys/fs/cgroup:ro --tmpfs /run --tmpfs /run/lock --net dockernetwork --ip 172.0.0.22 -p 8080:80 hathanhtamnd/image_name /sbin/init<br/><br/>

<i>- Access docker</i><br/>
docker exec -it <id container> bash<br/><br/>

<h1>For ssh</h1>

<i>- Create ssh key</i><br>
ssh-keygen -t rsa -b 4096 -C "thanhtam.ha1994@hotmail.com"<br/><br/>

<h1>For mysql</h1>

<i>- Create mysql user for all host</i><br/>
create user 'docker'@'%';<br/>
grant all on *.* to 'docker'@'%';<br/><br/>

<h1>For CentOS system</h1>

<i>- Set timezone</i></br>
sudo timedatectl set-timezone Asia/Ho_Chi_Minh<br/><br/>

<i>- Install OpenJDK 8</i><br/>
yum install -y java-1.8.0-openjdk-devel.x86_64<br/>
update-alternatives --config java<br/>

<i>- Install Postgresql 9.5</i><br/>
yum install -y http://yum.postgresql.org/9.5/redhat/rhel-7-x86_64/pgdg-redhat95-9.5-2.noarch.rpm<br/>
yum install -y postgresql95-server postgresql95<br/>
/usr/pgsql-9.5/bin/postgresql95-setup initdb<br/>
systemctl start postgresql-9.5<br/>
systemctl enable postgresql-9.5<br/>
su - postgres</br>
psql<br/>
\password<br/>
vim /var/lib/pgsql/9.5/data/pg_hba.conf<br/>
host all all 0.0.0.0/0 md5<br/>
vim /var/lib/pgsql/9.5/data/postgresql.conf
listen_addresses = '*'<br/><br/>

<i>- Install nginx</i><br/>
yum install -y epel-release<br/>
yum install -y nginx<br/>
systemctl enable nginx<br/>
systemctl start nginx<br/><br/>

<i>- Install firewall</i><br/>
yum install -y firewalld<br/>
systemctl unmask firewalld<br/>
systemctl enable firewalld<br/>
systemctl start firewalld<br/>
firewall-cmd --permanent --zone=public --add-service=http<br/>
firewall-cmd --permanent --zone=public --add-service=https<br/>
firewall-cmd --reload<br/>

<i>Install fuser</i><br/>
sudo yum install psmisc<br/>

<h1>For Ubuntu system</h1>

<i>- Set timezone</i></br>
sudo dpkg-reconfigure tzdata<br/>

<h1>For Docker Image</h1>
<i>- Tomcat</i><br/>
sudo docker pull tomcat:8.5.11-jre8-alpine<br/>
sudo docker run -d -v /var/www/xinhtv.com:/usr/local/tomcat/webapps --name tomcat -p 8888:8080 tomcat:8.5.11-jre8-alpine<br/>
mv target/xinh-tv-0.0.1-SNAPSHOT.war /var/www/xinhtv.com/ROOT.war<br/>
sudo docker restart tomcat<br/><br/>
<i>- httpd</i><br/>
sudo docker pull httpd:latest<br/>
sudo docker run -d -v /var/www/admin.xinhtv.com:/usr/local/apache2/htdocs/ --name httpd -p 8080:80 httpd:latest<br/>
<i>- Config rewrite module</i><br/>
Edit file go to httpd.conf<br/>
- Enable module<br/>
LoadModule rewrite_module modules/mod_rewrite.so<br/>
- Add Code to Root directory in httpd.conf<br/>
<!--<br/>
    Options Indexes FollowSymLinks<br/>
    Require all granted<br/>
    AllowOverride All<br/>
    RewriteEngine On<br/>
    RewriteCond %{REQUEST_FILENAME} !-f<br/>
    RewriteCond %{REQUEST_FILENAME} !-d<br/>
    RewriteRule . index.html [L]<br/>
--><br/>
