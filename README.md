## pyinfra-connector-lxcssh
pyinfra Connector for executing commands inside LXC (not lxd) containers using SSH to host.
Containers can be managed by root (sudo needed) or other users.
Inside the container execution is always as a root only.

## Instalation
* pip install pyinfra
* pip install git+https://github.com/opekar/pyinfra-dev/pyinfra.git

## Usage
    An inventory file (``inventory.py``) for connection to lxc container via lxc (not lxd):

    ```python

        hosts = [
            ("lxcssh/host_lxc:container_name"),
        ]
    ```

    pyinfra inventory.py deploy.py

    ```python

        hosts = [
            ("lxcssh/host_lxc:container_name", {"more ssh params here, or sudo relateing params"}),
        ]
    ```

    Another possibility:

    In this case we know that the container is manager by root user (even thought the container itself can be unpriviledged)
    ```bash
        pyinfra  @lxcssh/lxc_host.company.example:container --sudo  exec -- lsb_release -a
    ```

## Thanks
* this repos is based on 
    * https://github.com/pyinfra-dev/pyinfra-print-connector
    * pyinfra dockerssh connector
    * https://github.com/andreasscherbaum/ansible-lxc-ssh  - ansible lxc connector pluging
