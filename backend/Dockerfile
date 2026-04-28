FROM python:3.12-alpine3.23

WORKDIR /app

COPY app.py .

ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

RUN adduser -D -u 1000 app app && chown -R app:app /app

USER app

EXPOSE 8080

HEALTHCHECK --interval=10s --timeout=3s --start-period=5s --retries=3 \
    CMD wget -qO- http://127.0.0.1:8080 || exit 1

STOPSIGNAL SIGTERM

CMD ["python", "-u", "app.py"]
