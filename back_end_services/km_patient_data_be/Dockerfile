FROM python:3.9-alpine

# can pass this as a build argument, if nothing is passed
# the default of 'master' will be set
ARG PATIENT_BRANCH=master

# setting for ease of readibility for use in RUN command
ENV REPO=https://github.com/Craig-Edge/sa-kwikmedical-patient-data.git
ENV BRANCH=${PATIENT_BRANCH}

RUN apk update && \
apk add --no-cache git && \
git clone ${REPO} --branch ${BRANCH} /patient && \
pip install -r /patient/dependencies/requirements.txt && \
python /patient/sa_kwikmedical_patient_data/manage.py makemigrations && \
python /patient/sa_kwikmedical_patient_data/manage.py migrate --run-syncdb && \
python /patient/sa_kwikmedical_patient_data/manage.py populate_patient_data

CMD ["python", "/patient/sa_kwikmedical_patient_data/manage.py", "runserver", "0.0.0.0:8000"]
