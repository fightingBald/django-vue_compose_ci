FROM python:3.12-alpine

ENV PYTHONUNBUFFERED=1

WORKDIR /app

RUN apk update && apk add --no-cache \
    libpq \
    libpq-dev \
    build-base

COPY requirements.txt .
COPY entrypoint.sh /entrypoint.sh
RUN pip install --no-cache-dir -r requirements.txt

COPY . .
RUN chmod +x /entrypoint.sh
EXPOSE 8000

ENTRYPOINT ["/entrypoint.sh"]
