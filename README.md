# Move Docker containers between different hosts

# Stop the container   
```docker stop $CONTAINER```

# Create a new image   
```docker commit $CONTAINER $CONTAINER```

# Save image
```docker save -o $CONTAINER.tar $CONTAINER```

# Save the volumes (use ".tar.gz" if you want compression)
```docker-volumes.sh $CONTAINER save $CONTAINER-volumes.tar```

# Copy image and volumes to another host
```scp $CONTAINER.tar $CONTAINER-volumes.tar $USER@$HOST:```

# On the other host:
```docker load -i $CONTAINER.tar```
```docker create --name $CONTAINER [<PREVIOUS CONTAINER OPTIONS>] $CONTAINER```

# Load the volumes
```docker-volumes.sh $CONTAINER load $CONTAINER-volumes.tar```

# Start container
```docker start $CONTAINER```
