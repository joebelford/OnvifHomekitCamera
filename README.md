# OnvifHomekitCamera
Implementing ONVIF to HomeKit Camera proxy

## Adding Submodules

### HomekitADK
Execute:
```bash
git submodule add git@github.com:joebelford/HomeKitADK.git
cd HomeKitADK
git fetch
git switch submodule-base
cd ..
git commit -am "Added HomeKitADK submodule"
```

### homekit_camera
Perform the following steps from within the HomeKitADK repo:
```bash
cd Applications
git submodule add git@github.com:joebelford/homekit_camera.git Camera
cd Camera
git fetch
git switch feature-camera
cd ../..
git commit -am "Added homekit_camera submodule"
```

### ffmpeg
Execute:
```bash
git submodule add git://source.ffmpeg.org/ffmpeg
cd ffmpeg
git pull
cd ..
git commit -am "Added ffmpeg submodule"
```

## Set up build environment

## Building ffmpeg Docker image
Build this container before opening dev container.
Execute:
```bash
cd ffmpegDocker
docker build -t joeshouse/ffmpeg .

## Building Camera app
Once launched into the dev container, execute:
```bash
cd HomeKitADK
cd ..
make TARGET=Linux APPS=Camera DOCKER=0
```

## Reference
[ffmpeg guide](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu)
