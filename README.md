# Assignment-Task 1(Docker Networking)
"This part will test your understanding of Docker networking and how to use it to
connect Docker containers"


##Step1-(To create a new Docker network, run the given command)

docker network create my_network

22fee77e251b0f57bfadaa5bc98302f02ea947c1f8d68b97a10aec3694bba7c3


Step 2-(For running a container) also verify it by accessing at the local host.

docker run -d --name nginx_container --network my_network nginx

28d02d5882e30f69b7c318e820fc97206bc81f66b3190add186d9f5a24b559dc


Step3-(For runing a container)

docker run -d --name httpd_container --network my_network httpd

be7e559e1d7be152fe697a354c6e545112acf6d19b010350aee3c7a06c6e98a9



Step4-(Viewing network information)

docker network inspect my_network
[
    {
        "Name": "my_network",
        "Id": "22fee77e251b0f57bfadaa5bc98302f02ea947c1f8d68b97a10aec3694bba7c3",
        "Created": "2023-08-17T19:26:37.9872971Z",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": {},
            "Config": [
                {
                    "Subnet": "172.18.0.0/16",
                    "Gateway": "172.18.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {
            "28d02d5882e30f69b7c318e820fc97206bc81f66b3190add186d9f5a24b559dc": {
                "Name": "nginx_container",
                "EndpointID": "cda8e92284792d7f6c22c36f8d31c59fd0ba1274de43621cc269c13b0764c3ab",
                "MacAddress": "02:42:ac:12:00:02",
                "IPv4Address": "172.18.0.2/16",
                "IPv6Address": ""
            },
            "be7e559e1d7be152fe697a354c6e545112acf6d19b010350aee3c7a06c6e98a9": {
                "Name": "httpd_container",
                "EndpointID": "cad06e47a50a65c5ce76398b5d60e84899b880b0cd9f366413430a3ebe6d5c43",
                "MacAddress": "02:42:ac:12:00:03",
                "IPv4Address": "172.18.0.3/16",
                "IPv6Address": ""
            }
        },
        "Options": {},
        "Labels": {}
    }
]


Step5- (Stopping the container)

docker stop nginx_container

nginx_container



Step6-( removing the container)

docker rm nginx_container

nginx_container



Step7-(Again create a new container and verify it at the local host)

docker run -d --name nginx_container_2 --network my_network nginx

5446187071b59cf0b69bf982e7229d6bfb539d048c390d58fbf9766b3d8e534c



Step8-(Display of information of running containers)

docker container ls
CONTAINER ID   IMAGE     COMMAND                  CREATED              STATUS              PORTS     NAMES
5446187071b5   nginx     "/docker-entrypoint.…"   17 seconds ago       Up 16 seconds       80/tcp    nginx_container_2
be7e559e1d7b   httpd     "httpd-foreground"       About a minute ago   Up About a minute   80/tcp    httpd_container




Step9-(Stopping and removing all the containers at once)

docker container stop httpd_container nginx_container_2 && docker container rm httpd_container nginx_container_2

httpd_container
nginx_container_2
httpd_container
nginx_container_2
