FROM docker.io/python:3.9-alpine3.13

LABEL \
    org.opencontainers.image.created="2021-11-09 21:00:00" \
    org.opencontainers.image.authors="" \
    org.opencontainers.image.url="https://github.com/DevWhateverOps/application" \
    org.opencontainers.image.documentation="https://github.com/DevWhateverOps/application" \
    org.opencontainers.image.source="https://github.com/DevWhateverOps/application" \
    org.opencontainers.image.version="0.1.0" \
    org.opencontainers.image.revision="<COMMIT_SHA>" \
    org.opencontainers.image.vendor="DevWhateverOps" \
    org.opencontainers.image.licenses="t.b.d." \
    org.opencontainers.image.ref.name="t.b.d."

RUN pip install -r requirements.txt

RUN addgroup --gid 250321 --system appgroup \
    && adduser --uid 250321 --system appuser --ingroup appgroup

COPY --chown=appuser:appgroup . /app

WORKDIR /app

USER appuser

CMD ["python", "./main.py"]
