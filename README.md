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
