#stage1
FROM node:21 AS frontend-builder

#Working directory
WORKDIR /app

#copy all the data
COPY . .

#install all the packages
RUN npm install

#===========================================================

#stage2
FROM node:21-slim

WORKDIR /app

#copy the compressed data of stage1 to stage2
COPY --from=frontend-builder /app .

#copy enviornment variable
COPY .env.sample .env.local

#expose port
EXPOSE 5173

#run the frontend application
CMD ["npm", "run", "dev", "--", "--host"]

