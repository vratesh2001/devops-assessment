FROM python:3.12-slim

RUN apt-get update && apt-get install -y gcc python3-dev && rm -rf /var/lib/apt/lists/*

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

RUN groupadd -r django && useradd -r -g django django
RUN chown -R django:django /app
USER django


EXPOSE 8000


CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]