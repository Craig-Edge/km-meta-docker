FROM node:alpine3.17

ARG REGIONAL_BRANCH=master

ENV REPO=https://github.com/Craig-Edge/km-regional-hospital.git
ENV BRANCH=${REGIONAL_BRANCH}

RUN apk update && \
apk add --no-cache git && \
git clone ${REPO} --branch ${BRANCH} /regional-fe && \
npm install --prefix /regional-fe/km-regional && \
npm install axios --prefix /regional-fe/km-regional

# Start react app
CMD ["npm", "start", "--prefix", "/regional-fe/km-regional"]