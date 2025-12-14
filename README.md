# Develpod
A simple wrapper script around podman to make it easier to build container images and to run commands in them. Designed to make it easy to develop software in a containerized environment.

## Dependencies
- Podman
- Posix compliant shell
- Xorg/XWayland
- xxd

## How To Use
### 1. Install
Ensure that you have all the dependencies on your system, and that `podman` and `xxd` are available in your $PATH. Then put the `develpod` file wherever makes sense on your system, and ensure it is in your $PATH.

### 2. Build
Develpod associates container images with the current working directory. You must first create a file in the directory of your project named `Containerfile` which must be a Containerfile compatible with podman. This file can contain comments of the form `##DEVELPOD## [name] [command]` to add commands for develpod to run. Once this file is created in the desired directory, run `develpod build` to build the image of your new container. Note that this command also replaces any image already associated with the current directory.

### 3. Run
Once an image has been built, you can run the develpod commands added to the Containerfile by running `develpod [name]`. This will execute [command] in a temporary container made with the image associated with the directory that has an interactive terminal, is connected to the host's xserver, and has access to the current working directory under `/develpod`.

### 4. Cleanup
Once you are done with an image, run `develpod clean` to get rid of it.
