FROM python:3.11.13-slim-bookworm

WORKDIR /app

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y --no-install-recommends \
    build-essential \
    libpq-dev \
    netcat-traditional \
    wget \
    && rm -rf /var/lib/apt/lists/*

COPY requirements.txt /app/
RUN python -m pip install --no-cache-dir -r requirements.txt

COPY . /app

ADD https://raw.githubusercontent.com/vishnubob/wait-for-it/master/wait-for-it.sh /usr/local/bin/wait-for-it.sh
RUN chmod +x /usr/local/bin/wait-for-it.sh

EXPOSE 8000

# ENV DJANGO_SETTINGS_MODULE=config.settings.dev  # Set this via docker-compose

CMD ["/usr/local/bin/wait-for-it.sh", "db:5432", "--", "bash", "-c", "python manage.py migrate && python manage.py runserver 0.0.0.0:8000"]
