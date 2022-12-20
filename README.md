# r-docker-template
A template for the development of `R` projects, using:
  - `VS Code` as IDE.
  - `Docker` for containerization.
  - `remote-containers` plugin for developing inside the container.
  - `renv` for managing packages.

## Prerequisites

### Install Docker

- [for Mac](https://docs.docker.com/docker-for-mac/install/)
- [for Linux](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
- [for Windows](https://docs.docker.com/docker-for-windows/install/)

After following the instructions, remember running the following:
```
sudo groupadd docker
sudo usermod -aG docker $USER
```
You may need to logout/reboot before the changes come into effect.


### Install required extensions in VSCode:

- Docker: ms-azuretools.vscode-docker
- Remote - Containers : ms-vscode-remote.remote-containers
  - Documentation available [here](https://code.visualstudio.com/docs/remote/containers)


## Setup

### renv

After the docker image is built/rebuilt and the devcontainer is run for the first time, open `R` and run `renv::restore()`.

**Note**: The `devcontainer.json` configuration assumes that you have the renv library installed in your local
machine, and tries to mount your cache of installed librearies when running the container. This way,
different projects can share the same cache of files, optimizing time and storage space.
If this is not the case, or your chaché is stored in the default path, modify the `"mounts"` field
in `devcontainer.json`.


## Additional configurations

### Optional: Enable pre-commits

To enable pre-commits, run the shell script `setup_precommit.sh`.

### Optional: Install pandoc

If you plan to render rmarkdown files, `pandoc` must be externally installed. Just run the script `install_pandoc.sh` provided inside the `shell_scripts` folder.

**Note**: Currently this script is run by default in the _postCreateCommand_ phase.

### Optional: Install rstan

If you plan to use `Stan` or the `rethinking` R package, you must intstall `rstan`. Just run the script `rstan_instal.sh` provided inside the `shell_scripts` folder.
