FROM nvidia/cuda:9.0-runtime
LABEL maintainer "Michael Everett, Björn Lütjens <{mfe}, {lutjens}@mit.edu>"

##
# Disclaimer: This Dockerfile enables to run /scripts/ga3c_cadrl_demo.ipynb
# It is not expected to work w/ the ROS code
##

RUN apt update
RUN apt -y upgrade

# Install tensorflow-gpu w/ python3 
RUN apt update
RUN apt-get -y install python3 python3-pip python3-dev
RUN pip3 install tensorflow

# Import user environment variable
ARG user
ENV USER $user

# Install Jupyter notebook
RUN pip3 install ipython==5.7 ipykernel==4.10 jupyter

RUN pip3 install matplotlib==2.2.3

COPY ./entrypoint.sh /

# Make ports available to the outside world
# Jupyter
EXPOSE 8888
# TensorBoard
EXPOSE 6006

ENTRYPOINT ["/entrypoint.sh"]
CMD ["bash"]
