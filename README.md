# Generic S3 component for Home Assistant

A quick fork of the [AWS S3 component](https://github.com/home-assistant/core/tree/dev/homeassistant/components/aws_s3) by [
Tomáš Bedřich](https://github.com/tomasbedrich) which is not restricted to AWS domains and therefore can be used with compatible S3 providers.

Hopefully short-lived since this repo will be archived as soon as Home Assistant implements support for compatible S3 providers out of the box.

## Install

```
cd config   # where configuration.yaml lives
mkdir custom_components
cd custom_components
git clone https://github.com/svoop/generic_s3.git
ha core restart
```
<details>
<summary># Prefixes (optional)</summary>

In order to use Prefixes, you will need to enter a prefix when creating a new connection.
Pre-existing connections cannot be changed to include a new prefix.

When entering a prefix use the following syntax, making sure to include the trailing slash:

```
firstfolder/nextfolder/lastfolder/
```

For example, if you would like to use the location "backups/homeassistant/" within your bucket, the prefix in the setup pane would be:

```
backups/homeassistant/
```
</details>
