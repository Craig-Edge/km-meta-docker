FROM node:alpine3.17

ARG AMBULANCE_BRANCH=master

ENV REPO=https://github.com/Craig-Edge/km-ambulance-app.git
ENV BRANCH=${AMBULANCE_BRANCH}

RUN apk update && \
apk add --no-cache git && \
git clone ${REPO} --branch ${BRANCH} /ambulance-fe && \
npm install --prefix /ambulance-fe/km-ambulance-app && \
npm install axios --prefix /ambulance-fe/km-ambulance-app

# Start react app
CMD ["npm", "start", "--prefix", "/ambulance-fe/km-ambulance-app"]