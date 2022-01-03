#-----------------------------------------------------------------------------
FROM docker.io/python:3.10-alpine3.15 AS base

# Set Virtual ENV
ENV VIRTUAL_ENV=/venv
ENV PATH="$VIRTUAL_ENV/bin:$PATH"

#-----------------------------------------------------------------------------
FROM base AS builder

# Install dependencies:
COPY app/requirements.txt .

RUN python3 -m venv $VIRTUAL_ENV \
    && $VIRTUAL_ENV/bin/pip install --no-cache-dir --disable-pip-version-check -r ./requirements.txt

#-----------------------------------------------------------------------------
FROM base

# format of BUILD_TIMESTAMP: $(date --iso-8601=seconds)
ARG BUILD_TIMESTAMP="n.a."
ARG COMMIT_SHA="n.a."

LABEL \
    org.opencontainers.image.created="$BUILD_TIMESTAMP" \
    org.opencontainers.image.authors="" \
    org.opencontainers.image.url="https://github.com/DevWhateverOps/application" \
    org.opencontainers.image.documentation="https://github.com/DevWhateverOps/application" \
    org.opencontainers.image.source="https://github.com/DevWhateverOps/application" \
    org.opencontainers.image.version="0.1.0" \
    org.opencontainers.image.revision="$COMMIT_SHA" \
    org.opencontainers.image.vendor="DevWhateverOps" \
    org.opencontainers.image.licenses="t.b.d." \
    org.opencontainers.image.ref.name="t.b.d."

# Create user and group
ARG USER_ID="250321"
ARG GROUP_ID="250321"
RUN addgroup --gid $GROUP_ID --system appgroup \
    && adduser --disabled-password --no-create-home --uid $USER_ID --system appuser --ingroup appgroup

COPY --chown=appuser:appgroup --from=builder $VIRTUAL_ENV $VIRTUAL_ENV
COPY --chown=appuser:appgroup /app /app

WORKDIR /app
USER appuser

CMD ["python", "./main.py"]

