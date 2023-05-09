####################################################################
Microsoft PHP SQL Server Drivers - Microsoft ODBC 17
####################################################################

.. _ProcessFast: https://processfast.com/
.. |date| date:: %m/%d/%Y

:Authors: `ProcessFast`_
:Created:  05/09/2024
:Modified: |date|


********************************************************************
Purpose
********************************************************************

To save backup copies of all packages and dependencies, along with all required compiled PHP extension binaries in case Microsoft takes older versions offline like they have done before and/or in case their repository is down - which has also happened multiple times before.



********************************************************************
Install Instructions
********************************************************************

Installation instructions as shown on Microsoft's site. Just preserving here as well


====================================================================
Ubuntu 20.04
====================================================================

.. code-block:: bash

	if ! [[ "18.04 20.04 22.04" == *"$(lsb_release -rs)"* ]];
	then
	    echo "Ubuntu $(lsb_release -rs) is not currently supported.";
	    exit;
	fi

	sudo su
	curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

	curl https://packages.microsoft.com/config/ubuntu/$(lsb_release -rs)/prod.list > /etc/apt/sources.list.d/mssql-release.list

	exit
	sudo apt-get update
	sudo ACCEPT_EULA=Y apt-get install -y msodbcsql18
	# optional: for bcp and sqlcmd
	sudo ACCEPT_EULA=Y apt-get install -y mssql-tools18
	echo 'export PATH="$PATH:/opt/mssql-tools18/bin"' >> ~/.bashrc
	source ~/.bashrc
	# optional: for unixODBC development headers
	sudo apt-get install -y unixodbc-dev



********************************************************************
Links and References
********************************************************************

- `Install the Microsoft ODBC driver for SQL Server (Linux) <https://learn.microsoft.com/en-us/sql/connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server?view=sql-server-ver16&tabs=ubuntu18-install%2Cdebian17-install%2Cdebian8-install%2Credhat7-13-install%2Crhel7-offline>`_

