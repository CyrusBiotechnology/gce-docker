The scripts in this folder create, connect and destroy to a new virtual machine ruinning in google compute engine.

Prerequisites:

-	[Google Cloud SDK](https://cloud.google.com/sdk/)

Before you can use this scripts you need to be logged into your account:

```
gcloud auth login
```

And have authorization to crate VMs in the Cyrus project. If you haven't been authorized yet [email me](mailto:javier@cyrusbio.com).

Usage
-----

Create configuration file:

```
./docker-init.sh
```

Start the VM:

```
./docker-up.sh
```


To log into the VM:

```
./docker-ssh.sh
```

And to delete the VM:

```
./docker-delete.sh
```

**DON'T FORGET TO TRANSFER THE NEW IMAGES TO THE REGISTRY AND TO DELETE THE VM WHEN YOU ARE DONE!**
