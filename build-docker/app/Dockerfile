FROM node:12-alpine AS build-stage

WORKDIR /workspace
COPY app/ ./ 
RUN yarn install --production
RUN yarn build


FROM nginx:stable-alpine

COPY --from=build-stage /workspace/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
