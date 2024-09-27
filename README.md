# ns8-logitechmediaserver

## Warning
- This is currently alpha stage.
- Currently there is no nice way to add/upload your media files to the instance, out of the box
  it will only stream remote resources such as internet radio.
- If you know how to upload music files to your NS8 and move the into the 'music' volume of the instance
  and set the correct permissions, you can stream those as well.
- Currently i am working on adding SFTPGo service for direct access to the 'music' volume.
- The web interface is currently plain HTTP.
- The web interface is not protected by authentication. This can be setup from within the LMS web interface.


This module provides the [Logitech Media Server](https://hub.docker.com/r/lmscommunity/logitechmediaserver) for Nethserver 8.

The module is currently not utilizing Traefik proxy and uses fixed host port mapping, this means they have to be available.
For this reason only one instance per node is possible.

Ports mappings:
- 9000:9000/tcp   Configurable
- 9090:9090/tcp   Fixed
- 3483:3483/tcp   Fixed
- 3483:3483/udp   Fixed

## Install

Instantiate the module with:

    add-module ghcr.io/epetersen-lab/logitechmediaserver:latest 1

The output of the command will return the instance name.
Output example:

    {"module_id": "logitechmediaserver1", "image_name": "logitechmediaserver", "image_url": "ghcr.io/epetersen-lab/logitechmediaserver:latest"}

## Configure

Let's assume that the logitechmediaserver instance is named `logitechmediaserver1`.

Launch `configure-module`, by setting the following parameters:
- `<MODULE_PARAM1_NAME>`: <MODULE_PARAM1_DESCRIPTION>
- `<MODULE_PARAM2_NAME>`: <MODULE_PARAM2_DESCRIPTION>
- ...

Example:

    api-cli run module/logitechmediaserver1/configure-module --data '{}'

The above command will:
- start and configure the logitechmediaserver instance
- (describe configuration process)
- ...


See also the `systemd/user/logitechmediaserver.service` file.

This setting discovery is just an example to understand how the module is
expected to work: it can be rewritten or discarded completely.

## Uninstall

To uninstall the instance:

    remove-module --no-preserve logitechmediaserver1

## Testing

Test the module using the `test-module.sh` script:


    ./test-module.sh <NODE_ADDR> ghcr.io/epetersen-lab/logitechmediaserver:latest

The tests are made using [Robot Framework](https://robotframework.org/)

## UI translation

Translated with [Weblate](https://hosted.weblate.org/projects/ns8/).

To setup the translation process:

- add [GitHub Weblate app](https://docs.weblate.org/en/latest/admin/continuous.html#github-setup) to your repository
- add your repository to [hosted.weblate.org]((https://hosted.weblate.org) or ask a NethServer developer to add it to ns8 Weblate project
