docker build -t jenkis .


docker run -d --name jenkis-server -p 8080:8080 -p 50000:50000 -v jenkis_home:/var/jenkins_home -v //var/run/docker.sock:/var/run/docker.sock jenkis

docker run -d \
--name jenkis-server \
-p 8080:8080 \
-p 50000:50000 \
-v jenkis_home:/var/jenkins_home \
-v /var/run/docker.sock:/var/run/docker.sock \
jenkis




http://localhost:8080

계정이름 shawn4823
비밀번호 0105305Kim@

name KimJungHun



github id KimJungHun555
password 0105305Kim@

jenkis



