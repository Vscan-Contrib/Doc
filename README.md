# vscan

## Description
Vscan is a tool for quickly detecting systems affected by a CVE, whether fresh or not.

It consists of a server with a database of your choice (MySQL, PostgreSQL).

The server part contains an administration interface as well as an API dedicated to agents.

The server configuration is flexible and allows a large choice of configuration to best suit different needs.

The client part contains an agent to install on machines maintained by vscan.

The agent will not fix the CVE but will indicate to you in a precise way the possible impacts on your computer (servers or workstations) in order to allow you to reduce the time of correction of security breaches and thus to increase it .

