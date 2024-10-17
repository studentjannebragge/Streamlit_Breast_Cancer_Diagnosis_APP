# Use an official Python runtime as a parent image
FROM python:3.10

# Set the working directory in the container
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Add system-level dependencies for some Python packages
RUN apt-get update && apt-get install -y \
    build-essential \
    libssl-dev \
    libffi-dev \
    python3-dev \
    && rm -rf /var/lib/apt/lists/*

# Install any needed packages specified in requirements.txt
RUN pip install --upgrade pip setuptools wheel
RUN pip install -r requirements.txt

# Make port 8501 available to the world outside this container
EXPOSE 8501

# Define environment variable for Streamlit
ENV STREAMLIT_HOME /app

# Run Streamlit when the container launches
CMD ["streamlit", "run", "main.py"]
