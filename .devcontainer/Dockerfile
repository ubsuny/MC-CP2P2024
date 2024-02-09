# Use the specified Python base image
FROM python:3.11.5

# Set environment variables
ENV PIP_DISABLE_PIP_VERSION_CHECK=1 \
    PYTHONPATH=/workspace

# Install necessary packages
RUN pip install numpy scipy matplotlib pandas dask jupyter

# Set the working directory to /workspace
WORKDIR /workspace

# Copy the project files into the container
COPY . /workspace

# Expose any necessary ports (if applicable)
# EXPOSE <port_number>

# Default command to execute when the container starts
CMD ["bash"]
