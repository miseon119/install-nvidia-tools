# install-nvidia-tools

## Install NVIDIA Nsight Compute in Containers
 
You must have the NVIDIA repositories set up, which should be the default in any NGC container. 

install Nsight Compute in container:
```console
# apt-get update -y
# apt-get install -y nsight-compute-2020.1.0
```

versions available, use a command like the following:
```console
# apt-cache search nsight-compute
```


## Debian-based dockerfile build sample

```plain
RUN apt-get update -y && \
     DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
         apt-transport-https \
         ca-certificates \
         gnupg \
         wget && \
     rm -rf /var/lib/apt/lists/*
RUN  echo "deb https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64 /" > /etc/apt/sources.list.d/cuda.list && \
     wget -qO - https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/7fa2af80.pub | apt-key add - && \
         apt-get update -y && \
     DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
         nsight-compute-2020.1.0 && \
     rm -rf /var/lib/apt/lists/*
```


> The CLI generated report file could be opened and visualized on another machine with the GUI. 

[more](https://developer.nvidia.com/blog/using-nsight-compute-in-containers/)

