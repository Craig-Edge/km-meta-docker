FROM node:alpine3.17

ARG OPERATOR_BRANCH=master

ENV REPO=https://github.com/Craig-Edge/km-operator.git
ENV BRANCH=${OPERATOR_BRANCH}

RUN apk update && \
apk add --no-cache git && \
git clone ${REPO} --branch ${BRANCH} /operator-fe && \
npm install --prefix /operator-fe/emergency-call-app && \
npm install axios --prefix /operator-fe/emergency-call-app

# Start react app
CMD ["npm", "start", "--prefix", "/operator-fe/emergency-call-app"]