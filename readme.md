# TeamCity server with one agent using `docker compose`

## Instructions for .NET Core

#### Installing .net core on the agents

1. run `docker-compose exec teamcity-agent bash`
2. once inside the shell, install .net core as follows:
	1. add dotnet apt repos to `source.list.d` using the below command
		`sudo sh -c 'echo "deb [arch=amd64] http://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'` Make sure to use the http version, not the https for this ubuntu (14.04) image is so minimal it doesn't have the package `https-transport`

	2. add apt gpg keys `sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 417A0893`
	3. run apt update `sudo apt-get update`
	4. finally install the sdk, we are using version 1.0.1 of the sdk
		`sudo apt-get install dotnet-dev-1.0.1`


#### Restart TeamCity server and agents
you can go `docker-compose stop<service_name>` and `docker-compose start <service_name>` one by one, or all at once by omitting the `<service_name>`