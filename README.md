# MTT (Minimum Time Travel) simulations in Web-GIS

Follow the instructions below to install and run fire behaviour simulations based on the MTT algorithm through a Web-GIS application.The instructions will get you a copy of the project up and running on your local machine for development and testing purposes. The project inculdes a copy of the MTT Fire Behavior Libraries (more details in http://sbrittain.net/FB/FB_API.htm).

### Prerequisites


* [XAMPP](https://www.apachefriends.org/index.html) - The open source package for PHP development environment including Apache Web server
* [Python](https://www.python.org/) - The interpreted, object-oriented, high-level programming language
* [GeoServer](http://geoserver.org/) - The open source server for sharing geospatial data
* [MySQL](https://www.mysql.com/) - The open source relational database management system (RDBMS)
* [curl](https://curl.haxx.se/) - The command line tool and library for transferring data with URLs

* [GDAL](https://www.gdal.org) - The Geospatial Data Abstraction Library. Follow these instructions (https://sandbox.idre.ucla.edu/sandbox/tutorials/installing-gdal-for-windows) to install GDAL 


```
Give examples
```

### Install XAMPP

Install XAMPP and choose Apache, MySQL, PHP and phpMyAdmin as the only components to be installed. Choose an installation folder  where you have full access. If IIS is already used in your machine, open services.msc and disable the World Wide Web Publishing Service (W3svc). Ensure that both Apache and MySQL are running. 
Go to http://localhost/phpmyadmin/index.php?lang=en and click on User accounts. Click the Edit privileges link of the root user name of the localhost host name and change the password of the user.
Open the C:\xampp\phpMyAdmin\config.inc.php file and set the password in the $cfg['Servers'][$i]['password'] variable.


### Install Python

Install Python and ensure that the path to the python executables has been added to the PATH environmental variable. Please install mysqlclient (https://www.lfd.uci.edu/~gohlke/pythonlibs/#mysqlclient) by choosing the appropriate .whl file based on the Python version installled. Download the appropariate .whl file and install the library by typing:
```
pip install mysqlclient<version>.whl
```
and then type:
```
pip install mysql-connector
```

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

Variable name: GDAL_DATA

Variable value: C:\Program Files (x86)\GDAL\gdal-data

Say what the step will be

```
Give the example
```

And repeat

```
until finished
```

End with an example of getting some data out of the system or using it for a little demo

## Running the tests

Explain how to run the automated tests for this system

### Break down into end to end tests

Explain what these tests test and why

```
Give an example
```

### And coding style tests

Explain what these tests test and why

```
Give an example
```

## Deployment

Add additional notes about how to deploy this on a live system

## Built With

* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
* [Maven](https://maven.apache.org/) - Dependency Management
* [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds

## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 

## Authors

* **Nikos Athanasis** - *Initial work* - [athanasis](https://github.com/athanasis)


## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Hat tip to anyone whose code was used
* Inspiration
* etc
