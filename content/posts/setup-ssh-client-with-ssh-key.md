---
title: "Setup Ssh Client With Ssh Key"
date: 2023-02-06T23:32:07+10:00
categories:
    - SSH
---

## Setting up an SSH client with an SSH key

To set up an SSH client with an SSH key, follow these steps:

1. Generate a new SSH key pair on your local machine:
```
$ ssh-keygen -t rsa -b 4096
```

2. Copy the public key to the remote server:
```
$ ssh-copy-id user@remote-server
```

3. Test the connection to the remote server:
```
$ ssh user@remote-server
```

## Setting up proxy jumping for multiple-hop servers

To set up proxy jumping for accessing multiple-hop servers, follow these steps:

1. Open the SSH configuration file on your local machine:
```
$ nano ~/.ssh/config
```

2. Add the following configuration for each intermediate server:
```
Host intermediate-server-1
  HostName intermediate-server-1.example.com
  User user
  IdentityFile ~/.ssh/id_rsa
  ProxyJump intermediate-server-0

Host intermediate-server-0
  HostName intermediate-server-0.example.com
  User user
  IdentityFile ~/.ssh/id_rsa
```

3. Test the connection to the final destination server:
```
$ ssh user@final-destination-server
```

Note: Replace "user" with your actual username, "remote-server" with the actual hostname of the remote server, and "intermediate-server-0" and "intermediate-server-1" with the actual hostnames of the intermediate servers.





