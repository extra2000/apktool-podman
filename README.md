# apktool-podman

| License | Versioning | Build |
| ------- | ---------- | ----- |
| [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) | [![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release) | [![Build status](https://ci.appveyor.com/api/projects/status/hfk4iixa2jwg9o0y/branch/master?svg=true)](https://ci.appveyor.com/project/nikAizuddin/apktool-podman/branch/master) |

Apktool using Podman.


## Cloning and building

Clone repositories:
```
git clone https://github.com/extra2000/apktool-podman.git
git clone https://github.com/extra2000/apktool.git apktool-podman/src/apktool
```

Build:
```
cd apktool-podman/src
podman build -t extra2000/ibotpeaches/apktool .
```


## Example usage

Example how to reverse engineer https://f-droid.org/repo/com.maxistar.textpad_37.apk:
```
mkdir test
chcon -v -t container_file_t ./test
curl https://f-droid.org/repo/com.maxistar.textpad_37.apk -o ./test/com.maxistar.textpad_37.apk
podman run -it --rm -v ./test:/opt/test:rw --workdir /opt/test localhost/extra2000/ibotpeaches/apktool java -jar /opt/apktool/brut.apktool/apktool-cli/build/libs/apktool-cli-all.jar d ./com.maxistar.textpad_37.apk
```
