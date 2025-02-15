# Source of notebook builds: https://hub.docker.com/r/jupyter/scipy-notebook

Building dual-platform jupyter-lab containers for analyzing ELM output

# 1a. First build the main jupyter-lab container, e.g. Jupyter-Lab 3.3.2. Run this within the repo directory
docker buildx build --push -t serbinsh/ngeearctic_elm_containers:ngeearctic_jupyterlab_3.3.2 --no-cache  \
--platform linux/amd64,linux/arm64 -f docker/jupyter/Dockerfile_lab_3.3.2 .

# 1b. First build the main jupyter-lab container w/ GEE, e.g. Jupyter-Lab 3.3.2. Run this within the repo directory
docker buildx build --push -t serbinsh/ngeearctic_elm_containers:ngeearctic_jupyterlab_3.3.2_gee --no-cache  \
--platform linux/amd64,linux/arm64 -f docker/jupyter/Dockerfile_lab_gee_3.3.2 .

# 2a. Second build the elmlab container which includes all of the example notebooks. Run this within the repo directorys
docker buildx build --push -t serbinsh/ngeearctic_elm_containers:elmlab_3.3.2 --no-cache  \
--platform linux/amd64,linux/arm64 -f docker/jupyter/Dockerfile_elmlab_3.3.2 .

# 2b. Second build the elmlab container w/ GEE which includes all of the example notebooks. Run this within the repo directorys
docker buildx build --push -t serbinsh/ngeearctic_elm_containers:elmlab_gee_3.3.2 --no-cache  \
--platform linux/amd64,linux/arm64 -f docker/jupyter/Dockerfile_elmlab_gee_3.3.2 .