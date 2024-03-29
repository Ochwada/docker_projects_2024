# Use the official Miniconda image as a parent image
FROM continuumio/miniconda3

# Set the working directory within the container
WORKDIR /app

# Copy your environment.yml into the container
COPY environment.yml /app/environment.yml

#COPY .condarc /root/.condarc

# Create the Conda environment using your environment.yml
RUN conda env create -f /app/environment.yml

# Make the environment active by default
RUN echo "source activate geospatial" > ~/.bashrc
ENV PATH /opt/conda/envs/geospatial/bin:$PATH

# Expose the port Jupyter Lab runs on
EXPOSE 8888

# Run Jupyter Lab (or Notebook) on container startup
CMD ["conda", "run", "-n", "geospatial", "jupyter", "notebook", "--notebook-dir=/app", "--ip='*'", "--port=8888", "--no-browser", "--allow-root"]
