FROM python:3.8-slim

ENV PYTHONUNBUFFERED=True

WORKDIR /app
COPY requirements.txt .

RUN apt-get -y update
RUN apt-get -y install git 
RUN pip install --no-cache-dir -r requirements.txt

COPY . ./

CMD exec gunicorn --preload --bind :$PORT --workers 1 --threads 8 --timeout 0 _wsgi:app
