# MTT (Minimum Time Travel) simulations in Web-GIS

Follow the instructions below to install and run fire behaviour simulations based on the MTT algorithm through a Web-GIS application.The instructions will get you a copy of the project up and running on your local machine for development and testing purposes. The project includes a copy of the MTT Fire Behavior Libraries (more details in http://sbrittain.net/FB/FB_API.htm).

### Prerequisites

* [XAMPP](https://www.apachefriends.org/index.html) - The open source package for PHP development environment including Apache Web server
* [Python](https://www.python.org/) - The interpreted, object-oriented, high-level programming language
* [GeoServer](http://geoserver.org/) - The open source server for sharing geospatial data
* [MySQL](https://www.mysql.com/) - The open source relational database management system (RDBMS)
* [curl](https://curl.haxx.se/) - The command line tool and library for transferring data with URLs
* [GDAL](https://www.gdal.org) - The Geospatial Data Abstraction Library.  

### Extract content
Extract all content to a local folder. This folder will be named as <AEGIS_folder> from now on.

### Install XAMPP

Install XAMPP and choose Apache, MySQL, PHP and phpMyAdmin as the only components to be installed. Choose an installation folder  where you have full access. If IIS is already used in your machine, open services.msc and disable the World Wide Web Publishing Service (W3svc). The installation folder will be named as <xampp_installation_folder> from now on.

Ensure that both Apache and MySQL are running (i.e.start the services). 

Go to http://localhost/phpmyadmin/index.php?lang=en and click on User accounts. Click the Edit privileges link of the root user name of the localhost host name and change the password of the user.
Open the C:\xampp\phpMyAdmin\config.inc.php file and set the password in the $cfg['Servers'][$i]['password'] variable.

Copy the <AEGIS_folder>\aegis@github_htdocs folder to <xampp_installation_folder>\htdocs folder.

### Install MySQL

Download MySQL Installer from https://dev.mysql.com/downloads/installer/ and execute it. Choose the appropriate Setup Type for your system. Typically you will choose Developer Default to install MySQL server and other MySQL tools related to MySQL development, helpful tools like MySQL Workbench. Or, choose the Custom setup type to manually select your desired MySQL products. Complete the installation process by following the instructions. This will install several MySQL products and start the MySQL server.

### Install Python

Install Python and ensure that the path to the python executables has been added to the PATH environmental variable. Please install mysqlclient (https://www.lfd.uci.edu/~gohlke/pythonlibs/#mysqlclient) by choosing the appropriate .whl file based on the Python version installled. Download the appropariate .whl file and install the library by typing:
```
pip install mysqlclient<version>.whl
```
and then type:
```
pip install mysql-connector
```
and then type:
```
pip install pywin32
```
and then type:
```
pip install ConfigParser
```
Be sure to have the file <python_folder>\Lib\site-packages\win32\pywintypes36.dll (please note that “36” is the version of your Python installation). If you don’t have this file, take it from <python_folder>\Lib\site-packages\pywin32_system32\pywintypes36.dll and copy it into <python_folder>\Lib\site-packages\win32\


### Install curl

Install curl and ensure that the path to the bin folder has been added to the PATH environmental variable.

### Install GDAL

Open Python GUI and check the  version of your Python in the top right, e.g. MSC v. 1900 32 bit.
Go in http://www.gisinternals.com/release.php and choose the appropropriate GDAL and MapServer version. Clicking the link will take you to the list of binaries (installers) to download.
Locate the “core” installer, which has most of the components for GDAL.
After downloading your version, install GDAL with standard settings.
Next, return to the list of GDAL binaries and install the python bindings for your version of Python.

Under the System variables pane, find the ‘Path’ variable, then click on Edit. Go to the end of the box and copy and paste the following:
```
;C:\Program Files (x86)\GDAL
```

In the same System variables pane, click on “New” and then add the following in the dialogue box:

```
Variable name: GDAL_DATA

Variable value: C:\Program Files (x86)\GDAL\gdal-data

```
![alt text](https://sandbox.idre.ucla.edu/sandbox/wp-content/uploads/2015/02/2015-02-23-16_43_38-New-System-Variable.png)


Add one more new variable by clicking “New…”. Add the following in the dialogue box:

```
Variable name: GDAL_DRIVER_PATH

Variable value: C:\Program Files (x86)\GDAL\gdalplugins

```
For visual aid about the steps followed, follow these instructions (https://sandbox.idre.ucla.edu/sandbox/tutorials/installing-gdal-for-windows) to install GDAL.

### Install GeoServer

Ensure that JRE  (Java Runtime Environment) is installed in your machine. If not install it from here https://www.oracle.com/technetwork/java/javase/downloads/index.html.

Install the latest stable version of the GeoServer. Follow the wizard to install GeoServer and choose to be installed as a service. 
After installation, go to http://localhost:8080/geoserver and remove any unnecessary workspaces, stores and layers.


## Test your deployment

Test your deployment by following these screen shots.
![alt text](http://meteo.aegean.gr/github_pics/xamp_running.PNG)
![alt text](http://meteo.aegean.gr/github_pics/phpmyadmin_running.PNG)
![alt text](http://meteo.aegean.gr/github_pics/geoserver_running.PNG)
![alt text](http://meteo.aegean.gr/github_pics/gdal_translate.PNG)
![alt text](http://meteo.aegean.gr/github_pics/ogr2ogr.PNG)
![alt text](http://meteo.aegean.gr/github_pics/curl.PNG)

### Initialization

Under the System variables pane, find the ‘Path’ variable, click on “New” and then add a new System variable for the <AEGIS_folder> location:

```
Variable name: AEGIS_HOME

Variable value: <path_to_the_AEGIS_folder>

```

Open the config.txt file from <AEGIS_folder>. Specify  the following configuration parameters:
```
password = <password for connecting to local mysql RDBMS.>
user = <user for connecting to local mysql RDBMS.>
host = <hostname of the deployment>
database =<database name
geoserver_account = admin:geoserver
```
A typical configuration should be:
```
password = <password for connecting to local mysql RDBMS.>
user = root
host = 127.0.0.1
database =firesimulationsdb
geoserver_account = admin:geoserver
```

Execute the <AEGIS_folder>\initial_configuration\create_styles.bat file
Go to http://localhost/phpmyadmin and create a new database with the name firesimulationsdb with utf8-bin encoding.

Execute the SQL query in <AEGIS_folder>\initial_configuration\simulationinfo.sql through the GUI of the http://localhost/phpmyadmin.

Edit the <AEGIS_folder>\initial_configuration\uploadareas.bat batch file and modify the areas_path variable.
Save the file and execute the script.

## Test your deployment again
Test your deployment again by following these screen shots.
![alt text](http://meteo.aegean.gr/github_pics/areas_uploaded.PNG)

Open your  browser to http://localhost/aegis@github_htdocs/

![alt text](http://meteo.aegean.gr/github_pics/initial_deploy.PNG)

## Install MTT as a service

Open an cmd as an Administrator and type:

```
cd %AEGIS_HOME%
```
and then:
```
python MTTServiceClass.py install 

```


## Running MTT in debuging mode

Open an cmd as an Administrator and type:

```
mmc Services.msc
```
Find the mttservice service and disable it. Then type:

```
cd %AEGIS_HOME%
```
and then:
```
python MTTServiceClass.py debug 
```


## Final deployment

Enable Open an cmd as an Administrator and type:

```
cd %AEGIS_HOME%
```
and then:
```
python MTTServiceClass.py update 

```

and finally Open an cmd as an Administrator and type:
```
mmc Services.msc
```
Find the mttservice service and enable it.

## Screenshots
![alt text](http://meteo.aegean.gr/github_pics/arrivaltimeoutput1.PNG)
![alt text](http://meteo.aegean.gr/github_pics/arrivaltimeoutput2.PNG)
![alt text](http://meteo.aegean.gr/github_pics/arrivaltimeoutput3.PNG)
