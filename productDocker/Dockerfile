
#Build stage
FROM node:16-alpine AS builder
WORKDIR '/app'
COPY package*.json ./
RUN npm install 
COPY . .
#Runs test first then runs the dev env after test have ran 
CMD ["sh", "-c", "npm test && npm run dev"]

#Run phase
FROM nginx:alpine
#Copy the build artifact from the builder stage and the build out in app/dist
COPY --from=builder /app/dist /usr/share/nginx/html
