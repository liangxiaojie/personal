FROM node:6.9.5

RUN npm config set registry https://registry.npm.taobao.org

RUN npm install -g hexo-cli

ENV NODE_ENV production
ENV NODE_PORT 4000
ENV HEXO_GENERATE_WATCH true

WORKDIR /app

CMD ["hexo", "server"]

EXPOSE 4000
