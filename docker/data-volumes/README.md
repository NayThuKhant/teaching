- Build image from Dockerfile

```
docker build -t feedback-node Dockerfile
```

- Testing

	0. Run the container from image
		```
		docker run -p 3000:80 -d --name feedback-node --rm feedback-node
		```
		- -d [Detached mode]
		- --rm [Remove the container once stopped]
		- -p [Publish port]
	1) Access the application from, localhost:3000
	2) Submit feedback (title - hello, document text - hello)
	3) Access the submitted form, localhost:3000/feedback/hello.txt
	4) Stop the container
		```
		docker stop feedback-node
		```
	5) Re-access the submitted form, localhost:3000/feedback/hello.txt [Form does not exist since the form is stored in container, and container is destroyed once stopped due to --rm option]
	6) Re-run the container without -rm option
		```
		docker run -p 3000:80 -d --name feedback-node feedback-node
		```

	7) Repeat step 1 to 5 [Form will be existed even though we stop the container, because the container is not destroyed when stopped]


- Build image from DockerfileWithVolume

```
docker build -t feedback-node-with-volume -f DockerfileWithVolume .
```

1) Repeat the step 1 to 5, use the name `feedback-node-with-volume` [Now we are using volumes and you will see that the form is persisted in mounted volume]
