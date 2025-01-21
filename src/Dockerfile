from node:22.13.0 AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install --only=production
COPY . .
RUN npm run build
FROM nginx:alpine
# COPY --from=0 /app/build /usr/share/nginx/html
COPY --from=builder /app/build /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]