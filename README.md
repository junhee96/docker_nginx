ec2로 Django, nginx, Docker 구동방법
---------------------------------

1. 도커 설치
2. 권한 주기

    curl -fsSL https://get.docker.com/ | sudo sh  # 도커 설치   
    sudo usermod -aG docker $USER # 현재 접속중인 사용자에게 권한주기

3. Dockerfile(Python, 패키지등등 설정)
4. docker 이미지생성

    docker build -t awsproject/django .

5. docker 이미지 실행

    docker run -p 8000:8000  awsproject/django

6. nginx 2개 config(nginx.config, nginx-app.conf), Dockerfile(nginx 설정) 작성
7. docker 이미지생성

    docker build -t awsproject/nginx .

8. nginx dockek 이미지 실행

    docker run -p 80:80 awsproject/nginx

9. docker 이미지를 관리하는 툴 설치

    sudo curl -L https://github.com/docker/compose/releases/download/1.25.0-rc2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
    sudo chmod +x /usr/local/bin/docker-compose

10. docker-compose.yml 작성
11. Dockerfile 주석 처리 

#EXPOSE 80   
CMD ["nginx", "-g", "daemon off;"]   
#EXPOSE 8000   
#CMD ["python3", "manage.py", "runserver", "0.0.0.0:8000"]

12. uwsgi.ini 작성
13. dokcer-compose를 build하고 실행(up/down으로 관리)

    docker-compose up -d --build
