The scripts in this folder create, connect and destroy to a new virtual machine ruinning in google compute engine. The scripts implement five commands(init, up, ssh, stop, destroy) that resemble vagrant's behavior.

Prerequisites:

-	[Google Cloud SDK](https://cloud.google.com/sdk/)

Before you can use this scripts you need to be logged into your account:

```
gcloud auth login
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
