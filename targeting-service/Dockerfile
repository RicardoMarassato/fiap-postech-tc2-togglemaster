# APP BUILDER
FROM python:3.14-alpine3.24 AS builder

WORKDIR /app

RUN apk add --no-cache ca-certificates && \
    addgroup -g 10001 -S appgroup && \
    adduser -u 10001 -S -G appgroup appuser

COPY requirements.txt .

RUN pip install --no-cache-dir --user -r requirements.txt

COPY . .

FROM python:3.14-alpine3.24

# APP
WORKDIR /app

COPY --from=builder /etc/passwd /etc/passwd
COPY --from=builder /etc/group /etc/group
COPY --from=builder /root/.local /home/appuser/.local
COPY --from=builder /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/
COPY --chown=appuser:appgroup . .

ENV PATH=/home/appuser/.local/bin:$PATH
ENV PYTHONUSERBASE=/home/appuser/.local

USER appuser

EXPOSE 8003

CMD ["gunicorn", "--bind", "0.0.0.0:8003", "app:app"]
