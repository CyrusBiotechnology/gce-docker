The scripts in this folder create, connect and destroy to a new virtual machine ruinning in google compute engine. The scripts implement five commands(init, up, ssh, stop, destroy) that resemble vagrant's behavior.

Prerequisites:

-	[Google Cloud SDK](https://cloud.google.com/sdk/)
```
curl https://sdk.cloud.google.com | bash
```

Before you can use any of the gce-docker scripts you need to be logged into your account:

```
gcloud auth login
```

And you need to set your project:

```
glcoud config set project cyrusmolcloud
```

And have the scripts cloned locally:
```
git clone https://github.com/CyrusBiotechnology/gce-docker.git
```

Then add those to your path, for example in your .bashrc:
```
export PATH=/Users/lucasnivon/gce-docker:$PATH
```

Usage
-----

Create configuration file:

```
gce-docker-init
```

You can adjustthe settings of the instance by modifing the config_file.

Start the VM:

```
gce-docker-up
```

To log into the VM:

```
gce-docker-ssh
```

You can delete the machine and store the drives by running:

```
gce-docker-stop
```

If you run gce-docker-up in a folder were you run the stop script a new instance is going to be created and the saved drives will be attached to it.

To delete the VM and all the drives:

```
gce-docker-destroy
```
