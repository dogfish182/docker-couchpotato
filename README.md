# Dockerfile to set up Couchpotato on ARM based systems

The main goal of this Dockerfile is to easily set up Couchpotato using Docker on the Raspberry Pi 2/3 (or any compatible ARM chipset).

## Quick setup

`docker run -p 5050:5050 --name couchpotato -d -v /*custom_config_dir*:/config -v /*custom_data_dir*:/data -v /*movies_dir*:/movies -v /*download_dir*:/download rpi-couchpotato`

## More details

The command above runs the Docker image and sets a couple of custom paths.

* /config where the configuration is stored (it's advised to configure this so the configuration is stored outside of the container)
* /data where the database, logs, plugins and cache are stored (it's advised to configure this so the database is stored outside of the container)
* /movies should point to the location where CouchPotato should move downloaded movies to (e.g. a folder/nfs share on the host)
* /download should point to the location where (e.g. sabnzbd) downloads movies to be processed by CouchPotato (e.g. a folder/nfs share on the host)

Secondly the command exposes the container on port 5050, names it "couchpotato" and runs it detached (so it will run in the background).

## Build Docker container

`docker build -t rpi-couchpotato .`
