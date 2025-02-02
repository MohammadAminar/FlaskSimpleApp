FROM python:alpine

RUN mkdir /app
COPY ./app.py /app

WORKDIR /app

# RUN pip install -r requirements.txt
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

CMD gunicorn -b 0.0.0.0:5000 app:app
