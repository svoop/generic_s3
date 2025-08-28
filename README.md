> DEPRECATED:
> Please use the [S3-Compatible](https://github.com/PhantomPhoton/S3-Compatible) integration from HACS instead. It works fine e.g. with Hetzner Object Storage and many other S3 clones.

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

## Optional Details

<details>
<summary>Prefixes</summary>
<br>

In order to use Prefixes, you will need to enter a prefix when creating a new connection.
Pre-existing connections cannot be changed to include a new prefix.

When entering a prefix, use the following syntax, making sure to include the trailing slash:

```
firstfolder/nextfolder/lastfolder/
```

For example, if you would like to use the location "backups/homeassistant/" within your bucket, the prefix in the setup pane would be:

```
backups/homeassistant/
```

<br>
<details>

<summary>S3 IAM Policy</summary>
<br>

In order to get IAM working with read/write to the location that you would like, without allowing access to any other folders within the bucket an example IAM policy is shown below:

This policy assumes the following information:
  * A bucket with the name "myhomebackups"
  * A prefix of "backups/homeassistant"


```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:ListAllMyBuckets",
        "s3:GetBucketLocation"
      ],
      "Resource": "arn:aws:s3:::*"
    },
    {
      "Effect": "Allow",
      "Action": "s3:ListBucket",
      "Resource": "arn:aws:s3:::myhomebackups",
      "Condition": {
        "StringEquals": {
          "s3:prefix": [
            "",
            "backups/",
            "backups/homeassistant/"
          ]
        }
      }
    },
    {
      "Effect": "Allow",
      "Action": "s3:ListBucket",
      "Resource": "arn:aws:s3:::myhomebackups",
      "Condition": {
        "StringLike": {
          "s3:prefix": "backups/*",
          "s3:prefix": "backups/homeassistant/*"
        }
      }
    },
    {
      "Effect": "Allow",
      "Action": "s3:*",
      "Resource": "arn:aws:s3:::myhomebackups/backups/homeassistant/*"
    }
  ]
}
```

</details>
</details>
