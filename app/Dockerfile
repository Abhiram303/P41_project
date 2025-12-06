# build stage (optional for compiling; here just for cleanliness)
FROM python:3.11-slim as builder
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir --upgrade pip && \
    pip install --no-cache-dir -r requirements.txt

# runtime stage
FROM python:3.11-slim
# create non-root user
RUN useradd -m -u 1000 appuser
WORKDIR /app
# copy installed packages and app code
COPY --from=builder /usr/local/lib/python3.11/site-packages /usr/local/lib/python3.11/site-packages
COPY --from=builder /usr/local/bin /usr/local/bin
COPY . /app

# ensure ownership
RUN chown -R appuser:appuser /app

USER appuser
ENV PORT=8080
EXPOSE 8080
CMD ["python", "app.py"]
