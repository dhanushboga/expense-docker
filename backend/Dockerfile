#FROM node:20
FROM node:20.18.3-alpine3.21 AS builder
WORKDIR /opt/backend
COPY package.json ./
COPY *.js ./
RUN npm install

 

#ENV DB_HOST="localhost"

FROM node:20.18.3-alpine3.21
RUN addgroup -S expense && adduser -S expense -G expense && \
    mkdir /opt/backend && \
    chown -R expense:expense /opt/backend
ENV DB_HOST="mysql" 
WORKDIR /opt/backend
USER expense
copy --from=builder /opt/backend /opt/backend
CMD ["node","index.js"]