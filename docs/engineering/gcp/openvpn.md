# OpenVPN

A VPN server allows us to connect securely to the platform. We currently have two VPN servers in GCP under the following accounts:

- **troc-cluster-dev**
- **troc-cluster-prd**

Each of these VPN servers enables us to connect to the platform in their respective environments. We are currently using [OpenVPN-installer](https://github.com/angristan/openvpn-install) to manage the OpenVPN servers.

## Creating and Deleting Users in the VPN

To create or delete a user:

1. Connect to the VPN server: `ssh <username>@<ip-address>`. To obtain the IP address, check the Google Cloud UI.

2. Use the OpenVPN script to manage user creation or deletion. It is very intuitive; here is an example:

    ```shell
    mogaal@openvpn:~$ sudo /srv/openvpn-install.sh 
    Welcome to OpenVPN-install!
    The git repository is available at: https://github.com/angristan/openvpn-install

    It looks like OpenVPN is already installed.

    What do you want to do?
       1) Add a new user
       2) Revoke existing user
       3) Remove OpenVPN
       4) Exit
    Select an option [1-4]: 1

    Tell me a name for the client.
    The name must consist of alphanumeric character. It may also include an underscore or a dash.
    Client name: oslan

    Do you want to protect the configuration file with a password?
    (e.g. encrypt the private key with a password)
       1) Add a passwordless client
       2) Use a password for the client
    Select an option [1-2]: 1

    * Using SSL: openssl OpenSSL 3.0.8 7 Feb 2023 (Library: OpenSSL 3.0.8 7 Feb 2023)

    * Using Easy-RSA configuration: /etc/openvpn/easy-rsa/vars

    * The preferred location for 'vars' is within the PKI folder.
      To silence this message move your 'vars' file to your PKI
      or declare your 'vars' file with option: --vars=<FILE>
    -----

    Notice
    ------
    Keypair and certificate request completed. Your files are:
    req: /etc/openvpn/easy-rsa/pki/reqs/oslan.req
    key: /etc/openvpn/easy-rsa/pki/private/oslan.key
    Using configuration from /etc/openvpn/easy-rsa/pki/401e8d65/temp.d30a61f3
    Check that the request matches the signature
    Signature ok
    The Subject's Distinguished Name is as follows
    commonName            :ASN.1 12:'oslan'
    Certificate is to be certified until Mar 10 12:02:09 2026 GMT (825 days)

    Write out database with 1 new entries
    Data Base Updated

    Notice
    ------
    Certificate created at:
    * /etc/openvpn/easy-rsa/pki/issued/oslan.crt

    Notice
    ------
    Inline file created:
    * /etc/openvpn/easy-rsa/pki/inline/oslan.inline
    Client oslan added.

    The configuration file has been written to /home/mogaal/oslan.ovpn.
    Download the .ovpn file and import it in your OpenVPN client.
    mogaal@openvpn:~$
    ```


3. Share the `username.ovpn` file with the user and ask them to install it on their machine.


