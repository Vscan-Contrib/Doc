# Vscan Documentation

## Introduction

Vscan is an open source security software suite developed mainly in Python 3 compatible 3.8 and higher.
It is released under the GPLv3 license.
It is based on a SQL database and has many possible configurations and uses.

## Présentation

Vscan's mission is to meet several more or less specific needs. It is designed to be flexible and multi-platform.
It can be used as a preventive, passive, or active security element.

## Composition

Vscan consists of four main distinct software programs:
1. The backend server,
2. The API server,
3. The agent,
4. The web interface.

### The backend server
The backend server contains the vscan engine.
This engine has various possible functionalities detailed in the "Functions" page of this documentation.

It has the following roles:

* Interaction with the database.
* Management of CPE reference dictionaries ([see this link](https://www.cert-ist.com/public/fr/SO_detail?code=CPE))
* Management of software, operating system and hardware vulnerabilities ([see this link](https://fr.wikipedia.org/wiki/Common_Vulnerabilities_and_Exposures))
* Make correspondence between CVE and CPE to have a readable database.
* Reporting of security alerts when a vulnerability is published.



### The API server

The API server is an optional component, it is not installed by default when installing vscan via an rpm package.

Indeed, you are not obliged to install the API server when using vscan in passive/passive mode (see this mode below).

The API server is mandatory in case you use the active/active and active/passive modes as well as for the web interface.

It also allows interaction via third party software or even via scripts. It is therefore very easy to customize vscan's web interface or to create your own (see the api documentation for authentication methods and use).

# The agent

The vscan agent is also an optional component, it is used to perform interactions with the machines managed by vscan.

The API server must be installed for the agent to work.

The agent is mandatory for active/active and active/passive operation.


## vscan modes
It can be activated in three different ways:

1. Active/active mode
2. Active/passive mode
3. Passive/passive mode

### The active/active mode
The active/active mode has several possible uses. When this mode is set up, it allows the software installed on the machine in question to be reported, but also to perform a certain number of remote interactions on the machines.

This mode allows, among other things, to create procedures according to the machines to set up mitigation in case of an attack or suspicion (isolation of the machine, deactivation of certain components, operation in degraded mode, etc.).

It can also enable machine patching (disabled by default, in this mode you will have to activate it and in no case will the patches be deployed automatically).

### Active/passive mode
The active/passive mode is a mode where only the server is active, the agent tracks the OS, the software and the installed hardware but cannot intervene on the machine in question.
It allows the server to maintain a list of software and their versions on given environments. You can add procedures to get the versions via the web interface or via API.


### Passive/passive mode
This mode makes the server and the agent passive. The server serves as a CVE/CPE database, makes matches and reports alerts on software, operating systems or hardware that you ask it to follow.
In this mode you have no active agent on the client machines and no possibility to track the versions of the installed components.
