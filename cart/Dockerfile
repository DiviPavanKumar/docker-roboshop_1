FROM node:20-alpine3.21 as builder
WORKDIR /opt/server
COPY package.json .
COPY *.js .
RUN npm install

FROM node:20-alpine3.21
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
ENV REDIS_HOST="redis" \
    CATALOGUE_HOST="catalogue" \
    CATALOGUE_PORT="8080"
WORKDIR /opt/server
USER roboshop
COPY --from=builder /opt/server /opt/server
CMD ["node" , "server.js"]


# FROM node:20-alpine
# RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
# WORKDIR /opt/server
# COPY package.json .
# COPY *.js .
# RUN npm install
# RUN chown -R roboshop:roboshop /opt/server
# ENV REDIS_HOST="redis" \
#     CATALOGUE_HOST="catalogue" \
#     CATALOGUE_PORT="8080"
# USER roboshop
# CMD ["node" , "server.js"]