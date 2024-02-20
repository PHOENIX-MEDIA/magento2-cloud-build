# PHOENIX MEDIA Magento2 Cloud Build

## Purpose
Dockerfile, configurations and scripts to build Magento2 Docker images. The scripts in this repository allow to execute the steps described in the [Running Magento2 in Kubernetes Part 2 article on Medium](https://medium.com/swlh/running-magento2-in-kubernetes-part-2-building-the-docker-image-8516c0ed7d48).

## Installation
Install the Composer package:
```bash
composer require phoenix-media/magento2-cloud-build
```

Execute the shell script to move the files from the dist folder to the appropriate location within the composer installation:
```bash
vendor/bin/px-cloud-build-install.
```

## Customization
All files provided by this package can be customized. However, each update of the module will overwrite them again.
Therefore, carefully review all changes before committing them after an update.

## License
Each source file included in this distribution is licensed under [Open Software License v. 3.0 (OSL-3.0)](http://opensource.org/licenses/osl-3.0.php).
