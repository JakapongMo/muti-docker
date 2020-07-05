# multi-step build
FROM node:alpine
WORKDIR '/app'
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# run phase
FROM nginx
# This container need port map 3000
EXPOSE 3000
# Copy 1 file
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
# From destination path from nginx doc COPY every file
COPY --from=0 /app/build /usr/share/nginx/html


