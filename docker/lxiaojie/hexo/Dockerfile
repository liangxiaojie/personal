FROM node:6.9.5

RUN npm config set registry https://registry.npm.taobao.org

RUN npm install hexo-cli -g

WORKDIR /app
VOLUME  /app

ENV NODE_ENV production
ENV NODE_PORT 4000
ENV HEXO_GENERATE_WATCH true

COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]
CMD ["hexo", "server"]

EXPOSE 4000
