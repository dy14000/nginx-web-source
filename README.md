# nginx-web-source

https://github.com/dy14000/test-cicd.git 
test-cicd/ubuntu_nginx/Dockerfile
<< git clone >> 에서 주소 수정하면 됩니다

FROM ubuntu:focal

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install -y nginx git
RUN git clone https://github.com/dy14000/static_web_template.git  (git 주소 수정)
COPY nginx/sites-available/default /etc/nginx/sites-available/default
RUN cp -r static_web_template/* /usr/share/nginx/html/ 
             (git repo 이름)
CMD ["nginx", "-g", "daemon off;"]
EXPOSE 80
(필요에 따라 포트번호 변경가능)
