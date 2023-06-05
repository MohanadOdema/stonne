# Docker running instructions to integrate your own pytorch models and configuration files within the container 

## Volume Creation and Mounting onto the container during the run command
First, create a volume that can be mounted onto the docker image with every instantiation, enabling the save of data across multiple docker run instances:

```bash
docker volume create my-volume
```

Then, mount the volume `my-volume` into the `stonnesimulator/stonne-simulators` using the following command:

```bash
docker run -v my-volume:/my-data -it stonnesimulator/stonne-simulators
```

This makes `my-volume` from your local machine associated with a `my-data` folder within the container, allowing data reuse throughout multiple container runs. 

To move data to mounted volume, `my-data` within the container, use the following command:

```bash
docker cp activation_sparsity $CONTAINER_ID:/my-data
```

To move data back to a folder on the main machine

```bash
docker cp $CONTAINER_ID:/my-data ./$destination_folder 
```