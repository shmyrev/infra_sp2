FROM python:3.10-slim

WORKDIR /app

COPY requirements.txt /app

RUN pip install -r /app/requirements.txt --no-cache-dir

COPY ./ /app

CMD ["gunicorn", "api_yamdb.wsgi:application", "--bind", "0:8000" ] 
