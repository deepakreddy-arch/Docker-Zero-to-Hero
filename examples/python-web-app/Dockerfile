FROM ubuntu

# Update package lists and install necessary dependencies
RUN apt-get update && \
    apt-get install -y python3 python3-pip

# Set up the working directory
WORKDIR  /app

# Copy requirements.txt into the container
COPY requirements.txt /app

# Install dependencies in a virtual environment
RUN python3 -m venv venv && \
    . venv/bin/activate && \
    pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application code into the container
COPY devops /app/devops

# Set the entrypoint and default command
ENTRYPOINT ["venv/bin/python"]
CMD ["devops/manage.py", "runserver", "0.0.0.0:8000"]



