FROM python:3.8.2 AS builder
WORKDIR  /app
# Intall requirements
COPY ./Server/requirements.txt .
RUN pip install -r requirements.txt
# Copy source
COPY ./Server/ .
COPY .env ./.dotenv
# Intall local app package
RUN pip install -e .
WORKDIR /app/j4u_api
# Serve in production mode
CMD python cli.py fresh-start --seed-test && python cli.py wsgi-serve


