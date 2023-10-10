# oc-generators

JSON OC Generator Data used by wanderer.moe's OC Generators.

---

## Usage

These files are stored as `./[game-name]/list.json` under `./generators`. This data is then called by our [API](https://git.wanderer.moe/api) and used on our [site](https://wanderer.moe). Feel free to use this data for your own projects, please credit us if you do.

### Github Actions

Configuration for Github Actions is stored in `.github/workflows/deploy.yml`.

-   Each push to `main` will trigger deployment using `rclone` to the R2 Bucket, where the CDN is hosted.

### rclone & R2 Setup

The R2 bucket is synced using `rclone`.

-   The `RCLONE_CONFIG` environment variable is used to store the configuration for `rclone` - this is stored in the Github repository secrets. (encoded into Base64)

-   If you are to use this repository to base your own R2 bucket off of, you will need to change the `rclone` configuration to your own:

```
[r2]
type = s3
provider = Cloudflare
access_key_id = <access_key_id>
secret_access_key = <secret_access_key>
endpoint = https://<bucket_name>.r2.cloudflarestorage.com/
acl = private
```

-   The configuration above will give you access to all your R2 buckets, and will allow you to sync to them, you would specify like `r2:<bucket_name>` in the `rclone` command.
