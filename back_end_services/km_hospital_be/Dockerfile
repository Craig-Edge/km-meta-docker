FROM python:3.9-alpine

# can pass this as a build argument, if nothing is passed
# the default of 'master' will be set
ARG HOSPITAL_BRANCH=master

ENV REPO=https://github.com/Craig-Edge/kwikmedical-hospital.git
ENV BRANCH=${HOSPITAL_BRANCH}

RUN apk update && \
apk add --no-cache git && \
git clone ${REPO} --branch ${BRANCH} /hospital && \
pip install -r /hospital/dependencies/requirements.txt && \
python /hospital/hospital_data/manage.py makemigrations && \
python /hospital/hospital_data/manage.py migrate --run-syncdb && \
python /hospital/hospital_data/manage.py populate_hospital_data

CMD ["python", "/hospital/hospital_data/manage.py", "runserver", "0.0.0.0:8000"]
