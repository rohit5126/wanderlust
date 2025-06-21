#stage1
FROM node:21 AS backend-builder

#working directory
WORKDIR /app

#copy all the data
COPY . .

#install the packages
RUN npm i

#========================================================

#stage2
FROM node:21-slim

WORKDIR /app

#copy compressed data of stage1 to stage2
COPY --from=backend-builder /app .

#copy enviornment variable
COPY .env.sample .env

#expose port
EXPOSE 5000

#run the backend application
CMD ["npm", "start"]
