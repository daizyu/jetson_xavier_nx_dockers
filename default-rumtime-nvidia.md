## pre-procedure about default runtime "nvidia"

You need to setting platform nvidia for "docker buld" compilers and linkers.

Check your default runtime .
```bash
sudo docker info 2> /dev/null | grep -i runtime
```
If it isn't nvidia , please follow this steps.
Otherwise, make procudure will be stopped.
```
Runtimes: runc io.containerd.runc.v2 io.containerd.runtime.v1.linux nvidia
 Default Runtime: nvidia
```

```bash
sudo cp /etc/docker/daemon.json /etc/docker/daemon.json.back-20220710
sudo vi /etc/docker/daemon.json
```

***/etc/docker/daemon.json***
Please add ***"default-runtime": "nvidia"*** on the file.
```
{
    "default-runtime": "nvidia",
    "runtimes": {
        "nvidia": {
            "path": "nvidia-container-runtime",
            "runtimeArgs": []
        }
    }
}
```

Restart and check runtime.
``` bash
sudo systemctl restart docker
sudo docker info 2> /dev/null | grep -i runtime
```

A default runtime is changed to nvidia.
```
Runtimes: runc io.containerd.runc.v2 io.containerd.runtime.v1.linux nvidia
 Default Runtime: nvidia
```

