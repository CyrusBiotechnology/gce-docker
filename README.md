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
gcloud config set project cyrusmolcloud
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

You can adjust the settings of the instance by modifing the config_file.

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

GCE Service Authentication
-----

Docker containers created with these scripts are automagically authenticated with the Cyrus GCE service login. This means that you don't have to re-authenticate to access various utilities through gsutil. However, many utilities are accessed through a shadow docker instance via a set of aliases.

For example, for gsutil:

```
alias gsutil='(docker images google/cloud-sdk || docker pull google/cloud-sdk) > /dev/null;docker run -t -i --net=host -v /home/lucasnivon/.config:/.config google/cloud-sdk gsutil'
```

Therefore if you want to call gsutil inside a script you need to run it inside a docker container and setup access into that container from the host.
Here's an example setting up a call to gsutil to fetch some data and copy into a directory shared by the host:
```
docker run -t -i --net=host -v /home/lucasnivon/.config:/.config -v `pwd`/openeyeDL://openeyeDL google/cloud-sdk gsutil  cp gs://openeye/openeye\_ubuntu12_bakerlicense.tgz /openeyeDL
```
Note that the .config file is mounted as a volume, and that a subdir of the PWD ("openeyeDL") is mounted as a volume so you can extract data from the container on the host filesystem.
