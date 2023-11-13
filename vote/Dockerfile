# Use official python runtime base image
FROM python AS build
# Set the container application directory to /app
WORKDIR /app
# Add requirements.txt to container folder /app/requirements.txt 
COPY requirements.txt /app/requirements.txt
# Execute pip install -r requirements.txt
RUN pip install -r requirements.txt
# Copy our code from the current folder to /app inside the container
COPY app.py /app/app.py
# Make port 80 available for links and/or publish
EXPOSE 80
# Define the command to be run when launching the container : `python app.py`
RUN python app.py