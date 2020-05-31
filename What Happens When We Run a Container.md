let's have a quick understanding about what actually happens in the background when we run the docker container run command.

There is a misconception sometimes that Docker is really just running containers and that's its main job.

But there's actually so much that's happening in the background that it does in addition to those containers executing commands.

When we type docker container run, in the background it's actually going to look for the image that we specified at the end of that command.

You remember when we typed nginx at the very end, that was the name of the image we wanted to run as a new container.

So it's going to look for that locally in the image cache. If it doesn't find it there, it's going to hop over to Docker Hub, which is its default remote image repository.

By default, it'll look it up there and download it and store it in the image cache.

So, if we didn't specify a version -- and we didn't, we just typed in nginx -- but without specifying a version, it'll just choose the latest.

Then, once it's got that image and ready to go, it's going to start up a new container based on that image.

It's not going to make a copy of the image.

It's actually going to just start a new layer of changes, right on top of where that image left off, and it's going to customize the networking.

It's going to give it a specific virtual IP address that's inside a Docker virtual network. It's actually going to open up the port that we specified. If we didn't specify the Publish command, the --publish, it's not going to open up any ports at all.

Since we did the 80:80, that's telling it to take the port 80 on the host and forward all that traffic to the port 80 in the container. Then that container finally will actually start using a command specified in the Dockerfile.

You can actually change a majority of these commands from the command line.

These are all really defaults.

We can actually specify the version of our image.

We can specify different ports or the default command to run when it starts that container.

But since we had a very simple command, it just used a lot of defaults coming out of the box.

As you can see, definitely a lot going on the background.
