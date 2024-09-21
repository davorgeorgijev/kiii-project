FROM node:20.15.1
WORKDIR /booking-frontend
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["npm", "start", "--", "--host", "0.0.0.0"]