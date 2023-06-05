# Raspberry Pi file transfer (FTP) and security shell (SSH) client setup

!> We assume, that IP-address of Raspberry Pi is _192.168.100.10_ (default). If you changed this IP-address, you should use it instead of the default one.

## File transfer (SFTP) utility installation

We will use special utility XFTP to implement file transfer, download it by link below:

:open_file_folder: [XFTP](https://1drv.ms/u/s!Am_hkdn5bouShAMvxxxOMKYij_GX)

Install the application and open it. Press "New" button and apply the following settings:

| Parameter                  | value          |
|----------------------------|----------------|
| **FTP Site parameters:**   |                |
| Name                       | 192.168.100.10 |
| Host                       | 192.168.100.10 |
| Protocol                   | SFTP           |
| Port Number                | 22             |
| Proxy Server               | None           |
| **Login parameters:**      |                |
| Use authentification agent | NO             |
| Method                     | Password       |
| User Name                  | pi             |
| Password                   | raspberry      |

After setup press mouse double click on recently created connection and new windows must  appear. It is consisted of two panels: left one contains a file system of the local PC (laptop), and the right one - file system of the target Raspberry Pi. This is a way for file exchange.


## Remote command line utility installation (SSH)

We will use special utility Xshell to implement SSH (remote control using special generic unix console), download it by link below:

:open_file_folder: [Xshell](https://1drv.ms/u/s!Am_hkdn5bouSg3APqv7imNzFDFk3)

Install the application and open it. Press "New" button and apply the following settings:


| Parameter                 | value          |
|---------------------------|----------------|
| **Connection:**           |                |
| Name                      | 192.168.100.10 |
| Host                      | 192.168.100.10 |
| Protocol                  | SSH            |
| Port Number               | 22             |
| **Authentification:**     |                |
| Method                    | Password       |
| User Name                 | pi             |
| Password                  | raspberry      |

After setup press mouse double click on recently created connection and new SSH windows must appear.


