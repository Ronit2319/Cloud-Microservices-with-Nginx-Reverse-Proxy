FROM python:3.11-slim
RUN apt-get update && apt-get install -y curl
WORKDIR /app
COPY . .
RUN pip install flask
EXPOSE 8002
CMD ["python", "app.py"]
