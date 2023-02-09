# this Repo is convert the demo js-s3-component repo to typescript version
https://github.com/pulumi/examples/tree/master/aws-js-s3-folder-component

  Create a new stack:

    ```bash
    $ pulumi stack init website-component-testing
    ```

1.  Set the AWS region:

    ```
    $ pulumi config set aws:region us-west-2
    ```

1.  Restore NPM modules via `npm install` or `yarn install`.

1.  Run `pulumi up` to preview and deploy changes.  After the preview is shown you will be
    prompted if you want to continue or not.

    ```bash
    $ pulumi up
    Previewing update of stack 'website-component-testing'
    Previewing changes:
    ...

    Updating stack 'website-component-testing'
    Performing changes:

        Type                       Name                                                  Status      Info
    +   pulumi:pulumi:Stack        aws-js-s3-folder-component-website-component-testing  created
    +   └─ examples:S3Folder       pulumi-static-site                                    created
    +      ├─ aws:s3:Bucket        pulumi-static-site                                    created
    +      ├─ aws:s3:BucketPolicy  bucketPolicy                                          created
    +      ├─ aws:s3:BucketObject  favicon.png                                           created
    +      └─ aws:s3:BucketObject  index.html                                            created

    ---outputs:---
    info: 6 changes performed:
        + 6 resources created
    Update duration: ***

    Permalink: https://app.pulumi.com/***
    ```

1.  To see the resources that were created, run `pulumi stack output`:

    ```bash
    $ pulumi stack output
    Current stack outputs (2):
        OUTPUT                                           VALUE
        bucketName                                       s3-website-bucket-***
        websiteUrl                                       ***.s3-website-us-west-2.amazonaws.com
    ```

1.  To see that the S3 objects exist, you can either use the AWS Console or the AWS CLI:

    ```bash
    $ aws s3 ls $(pulumi stack output bucketName)
    2018-04-17 15:40:47      13731 favicon.png
    2018-04-17 15:40:48        249 index.html
    ```

1.  Open the site URL in a browser to see both the rendered HTML and the favicon:

    ```bash
    $ pulumi stack output websiteUrl
    ***.s3-website-us-west-2.amazonaws.com
    ```

1.