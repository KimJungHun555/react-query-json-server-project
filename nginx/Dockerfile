# Nginx 공식 이미지 사용
FROM nginx:alpine

# 로컬의 nginx 설정 파일을 컨테이너 내 설정 경로로 복사
COPY nginx.conf /etc/nginx/conf.d/default.conf

# 빌드된 정적 파일을 Nginx가 읽을 수 있는 경로로 복사
# (경로는 프로젝트 빌드 설정에 따라 다를 수 있음)
COPY ./dist /usr/share/nginx/html

# 80 포트 개방
EXPOSE 80

# Nginx 실행
CMD ["nginx", "-g", "daemon off;"]