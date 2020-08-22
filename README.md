# Global Variables

Simple native application for reading global variables from global JSON configuration file.

## Ho wto use it

Application can be used like this:

`$ vars --source=/path/to/json/file.json CATEGORY.CATEGOY.CATEGORY.KEY`

Where we have passed the source JSON file and variable path. 

Or:

`$ vars CATEGORY.CATEGOY.CATEGORY.KEY`

Where default JSON path is: 

`/root/Server/Variables/Configuration.json`

## Building the application

To build application perform the following steps:

-  cd into project directory
- mkdir build
- cd build
- cmake ..
- make
- make install

### Building requirements

The following dependencies needed in order to be able to build the application:

- C++ installed for the platform
- Cmake, Make and proper C++ compiler
- Boost library version >= 1.71.0.

# Example JSON configuration

The following example illustrate valid JSON variables configuration: 

```json
{
  "variables": {
    "SERVER": {
      "CERTIFICATION": {
        "HOME": "{{SERVER.SERVER_HOME}}/Server/Ca",
        "CERTIFICATES": "/etc/ssl/certs"
      }
    },
    "SERVICE": {
      "DATABASE": {
        "NAME": "postmaster_db",
        "PORTS": {
          "PORT": 5432,
          "PORT_EXPOSED": 35432
        },
        "TYPE": "Postgres",
        "HOST": "127.0.0.1",
        "DB_DIRECTORY": "mail_directory",
        "TABLE_DOMAINS": "mail_virtual_domains",
        "TABLE_USERS": "mail_virtual_users",
        "TABLE_ALIASES": "mail_virtual_aliases",
        "VIEW_DOMAINS": "mail_view_domains",
        "VIEW_USERS": "mail_view_users",
        "VIEW_ALIASES": "mail_view_aliases"
      },
      "MEMORY_DATABASE": {
        "NAME": "postmaster_mem_db",
        "PORTS": {
          "PORT": 6379,
          "PORT_EXPOSED": 36379
        },
        "TYPE": "Redis",
        "HOST": "127.0.0.1"
      },
      "MAIL_SEND": {
        "NAME": "postmaster_send",
        "PORTS": {
          "PORT_ANTI_VIRUS": 10025
        }
      },
      "MAIL_RECEIVE": {
        "NAME": "postmaster_receive",
        "MAILBOXES_CAPACITY": "30G",
        "PORTS": {
          "PORT_EXPOSED_IMAP": 3143,
          "PORT_EXPOSED_IMAPS": 3993,
          "PORT_EXPOSED_POP": 3110,
          "PORT_EXPOSED_POP3S": 3995
        }
      },
      "ANTI_VIRUS": {
        "NAME": "postmaster_antivirus",
        "PORTS": {
          "PORT": 10024
        }
      },
      "ANTI_SPAM": {
        "NAME": "postmaster_antispam",
        "PORTS": {
          "PROXY": 11332,
          "WORKER": 11333,
          "WEBUI": 11334,
          "WEBUI_EXPOSED": 11334
        }
      },
      "NETWORK": {
        "NAME": "postmaster_network",
        "SUBNET": "172.18.0.0/16"
      }
    }
  }
}
```

Accessing to some variables can be done like this:

`vars SERVICE.DATABASE.PORTS.PORT_EXPOSED`

Output of the command would be:

`35432`