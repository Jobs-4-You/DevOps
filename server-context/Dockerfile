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
COPY wait-for-it.sh wait-for-it.sh
RUN chmod +x wait-for-it.sh
# Serve in production mode
CMD ./wait-for-it.sh db:5432 -- python cli.py wsgi-serve


