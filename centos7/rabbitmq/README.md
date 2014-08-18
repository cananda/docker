= docker-rabbitmq based on centos7

Docker image to run a RabbitMQ server built on official CentOS 7.0 base image


Usage
-----

To create the image `centos7/rabbitmq`, execute the following

	$ sudo docker build -t centos7/rabbitmq .


Running the RabbitMQ server
---------------------------

Run the following command to start rabbitmq:

	$ sudo docker run -d -p 5672:5672 -p 15672:15672 centos7/rabbitmq

The first time that you run your container, a new random password will be set.
To get the password, check the logs of the container by running:

	$ docker logs <CONTAINER_ID>

You will see an output like the following:

	========================================================================
	You can now connect to this RabbitMQ server using, for example:

	 $ rabbitmqadmin -u admin -p 5elsT6KtjrqV -H <host> -P <port> list vhosts

	Please remember to change the above password as soon as possible!
	========================================================================

In this case, `5elsT6KtjrqV` is the password set. 
You can then connect to RabbitMQ:

	$ rabbitmqadmin -u admin -p 5elsT6KtjrqV -P 15672 list vhosts

Done!


Setting a specific password for the admin account
-------------------------------------------------

If you want to use a preset password instead of a randomly generated one, you can
set the environment variable `RABBITMQ_PASS` to your specific password when running the container:

	$ sudo docker run -d -p 5672:5672 -p 15672:15672 -e RABBITMQ_PASS="mypass" centos7/rabbitmq

You can now test your new admin password:

	$ rabbitmqadmin -u admin -p mypass -P 15672 list vhosts

Credits: https://github.com/tutumcloud/tutum-docker-rabbitmq
