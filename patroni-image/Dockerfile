# Use an official Python runtime as a parent image
FROM python:3.9-slim

# Set the working directory in the container
WORKDIR /usr/src/app

RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y gcc libpq-dev

# Install PostgreSQL
RUN apt-get update && apt-get install -y postgresql

# Install psycopg2
RUN pip install psycopg2-binary

# Install Patroni
RUN pip install --no-cache-dir -vvv patroni

# Copy the local configuration file into the container
COPY patroni.yml .

# Make port 8008 available to the world outside this container
EXPOSE 8008

# Define environment variable
ENV NAME World

# Run patroni when the container launches
CMD ["patroni", "./patroni.yml"]