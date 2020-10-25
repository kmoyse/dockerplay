# docker openssh _server

# build

Build the image

`cp ~/.ssh/id_rsa.pub .`

Give name that will match dockerhub-ib/name

`docker build -t kmoyse/akgs_sshd .`

# Run a test_sshd container

Then run it. You can then use docker port to find out what host port the container’s port 22 is mapped to:

`docker run -d -P --name test_sshd akgs_sshd`

`docker port test_sshd 22`
0.0.0.0:32768


`ssh root@0.0.0.0 -p 32768`

root@9202657cc4b6:~# java -version
openjdk version "1.8.0_252"
OpenJDK Runtime Environment (build 1.8.0_252-8u252-b09-1ubuntu1-b09)
OpenJDK 64-Bit Server VM (build 25.252-b09, mixed mode)

`ssh akigrafsoft@0.0.0.0 -p 32769 java -version`
The authenticity of host '[0.0.0.0]:32769 ([0.0.0.0]:32769)' can't be established.
ECDSA key fingerprint is SHA256:0oivuJLqLALGe/ysuKmrWNLw4SlBljvwcs6SmbMOBbU.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[0.0.0.0]:32769' (ECDSA) to the list of known hosts.
openjdk version "1.8.0_252"
OpenJDK Runtime Environment (build 1.8.0_252-8u252-b09-1ubuntu1-b09)
OpenJDK 64-Bit Server VM (build 25.252-b09, mixed mode)


# upload to docker hub (id:kmoyse)

`sudo docker login`
kmoyse:A.77T.
`sudo docker push "kmoyse/akgs_sshd:latest"`



