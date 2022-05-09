# Docker basic commands
### Sets of commands for using Docker on Centos linux distribution:
**Note**: _it's recommended to run this commands as `root` user or you should insert `sudo` before each command_.

Start Docker platform on your local machine:

`systemctl start docker`

Check if Docker running properly on your local machine:

`systemctl status docker`

Create a container from `hello world` image and start the container on your local machine:

`docker run hello-world`

If you get the message `Hello from Docker!` then the container runs successfully.

Check the currently running containers on your local machine:

`docker ps`

You can add the option `-a` to view the previously running containers on your machine:

`docker ps -a`

It will show detailed info about each container previously running:

<pre>CONTAINER ID   IMAGE         COMMAND    CREATED          STATUS                      PORTS     NAMES
91582e45d7cc   ubuntu        &quot;bash&quot;     4 minutes ago    Exited (0) 11 seconds ago             agitated_pascal
949dcd991d2b   hello-world   &quot;/hello&quot;   49 minutes ago   Exited (0) 49 minutes ago             objective_dubinsky
</pre>

As you see it gives you info about `CONTAINER ID`, `Image Name` and `Instance Name` of the container.


Check container images on your machine:

`docker images`

It will show detailed info about each container image:

<pre>REPOSITORY    TAG       IMAGE ID       CREATED        SIZE
ubuntu        latest    d2e4e1f51132   9 days ago     77.8MB
hello-world   latest    feb5d9fea6a5   7 months ago   13.3kB
</pre>

Get container `image` ubuntu locally or pull it from Docker hub then Create a container from the image and start the container on your machine then enter the interactive bash remotely on the container:

`docker run -it ubuntu bash`

if you get `root@2dff4fba5d4f:/#` then you are now on the running container bash.

you can run `ls` to check the directories of the current `ubuntu` container:

`bin  boot  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var`

To check home directory contents:

`ls -asl home`

We will create new folder on `home` directory called `lab`:

`cd home`

`mkdir lab`

We can check that `lab` directory created on `home`:

`ls`

Then we will create file on the `lab` directory called `container.txt` and we will write on it `"ubuntu container instance"`:

`cd lab`

`echo "ubuntu container instance" -> container.txt`

Check if the file created by running command:

`cat container.txt`

It will output :

`ubunto container instance`

Now after we create the new directory and file on ubuntu container we will exit from this container it will stop running directly:

`exit`

After exiting the container we can confirm that it stop running by:

`docker ps `

Then we will start ubuntu container another time:

`docker run -it ubuntu bash`

If we check the home directory now:

`ls -asl home`

We will not find lab directory and the file we created previously because each time we run ubuntu image we create new instance of the container.

we can check that by running:

`docker ps -a`

It will show these instances of `ubuntu` container:

`CONTAINER ID   IMAGE         COMMAND    CREATED          STATUS                      PORTS     NAMES
91582e45d7cc   ubuntu        "bash"     4 minutes ago    Exited (0) 11 seconds ago             agitated_pascal`

`bc56e9119461   ubuntu        "bash"     20 minutes ago   Exited (0) 7 minutes ago              gracious_agnesi`
 
To check the previous ubuntu container instance which we created lab directory on it:

First we start the ubuntu container instance we can find the name of the instance from the table `gracious_agnesi`:

`docker start gracious_agnesi`

Then we enter the container instance bash using command:

`docker attach gracious_agnesi`

Now we can check the current container instance directory:

`ls home -asl`

It will show that the lab directory there then we check if the file container.txt is there:

`ls home/lab -asl`

It will show the file is still there, so as you see that each instance of `ubuntu` container has it's own state also it's separated from each other and that's one of the important features of containers technology.

**Made with ❤ by Mohamad Oghli**

I will update on it so check the GitHub repository.

Email:
`mhd.sh.oghli@gmail.com`



