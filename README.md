# Kubeflow Rocks

Collection of [rocks](https://canonical-rockcraft.readthedocs-hosted.com/en/latest/explanation/rocks/) for Kubeflow components.

# Development notes
- Rockcraft tutorial:
  https://canonical-rockcraft.readthedocs-hosted.com/en/latest/tutorials.html
- Example:
  https://github.com/jnsgruk/seldon-core-operator-rock
- Use `stage-packages` to install required packages for application to run.
- Use `build-environment` to setup environment variables for build stage.
- Use `build-packages` and `build-snaps` for build stage. Those will not be used by application. As a result, if build and application require the same package, it needs to be in both `build-packages` and `stage-packages`
- If issues with LXD/Docker arise review firewall setup:
  https://linuxcontainers.org/lxd/docs/master/howto/network_bridge_firewalld/
- While building rocks these commands are very helpful:
  ```
  rockcraft clean
  lxc --project rockcraft image list
  ```
- The rock's entrypoint is [Pebble](https://canonical-rockcraft.readthedocs-hosted.com/en/latest/explanation/pebble/). At this point, there is no way to specify other entrypoint. A Pebble layer is added via adding the `001-deafault.yaml` file to `/var/lib/pebble/default/layers/` (Rockcraft does that). Refer to source code for more details.

# Building Rocks

To build rocks for Kubeflow components:
```
cd <image-directory>
rockcraft pack
```

# Testing

