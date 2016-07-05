
# Vireo test vm

This is a Vagrant repo for bring up a test instance of Vireo ETD software.
It includes the option of installing [E-Prints](http://eprints.org) to test
and identify integration issues.

## Requirements under Ubuntu 16.04 LTS

+ Java >= 8 (openjdk 1.8)
+ PostgreSQL >= 9
+ Ubuntu Packages
    + default-jdk-8
    + postgress, postgres-contrib
    + git
    + ant, ant-optional
    + ivy, ivyplusplus
    + curl
    + zip/unzip
    + doxygen
+ Compiled
    + playframework 1.3.4
    + Vireo 3.0.6

## Vireo Notes

1. Install the debian packages
2. Clone playframework and Vireo from Github
3. Build play1/framework with Ant
4. Build Vireo with Play
5. Configure Vireo
    + You will need to setup the database and DB user in Postgres
        + sudo -u postgres createuser -dSRP vireo
        + sudo -u postgres createdb -U vireo -h localhost vireo
    + You will also need to edit the conf/application.conf appropiately
        + Set hostname for app (usually localhost if testing) 
        + Set DB connection (db hostname, db user/password, database name)
5. "Run" Play on Vireo so that initial user gets created
    + play run /home/vagrant/Vireo
7. After that Vireo can be "played" as a service with start, pid and stop
    + play start /home/vagrant/Vireo
    + play pid /home/vagrant/Vireo
    + play stop /home/vagrant/Vireo

### Vireo reference links

+ [Vireo Install](https://github.com/TexasDigitalLibrary/Vireo/wiki/Install) - Claims it has been tested with MySQL 5.5
+ [MySQL/JDBC Setup under Ubuntu](https://help.ubuntu.com/community/JDBCAndMySQL)
+ [Configuring Vireo 2.0](http://www.scottphillips.com/2012/12/configuring-vireo-2-0/) - Talks about MySQL configuration
+ [Jarrow, Electronic Thesis, and Dissertation Software](http://journal.code4lib.org/articles/7486) - old article survey ETD package options

## EPrints Notes

Installing EPrints is a three step process.  You run the same script each time
providing the step number you're on.

```
    # As vagrant user
    bash /vagrant/setup-eprints.sh 1
    # eprints user
    sudo su eprints
    bash /vagrant/setup-eprints.sh 2
    exit
    # As vagrant user again
    bash /vagrant/setup-eprints.sh 3
```

#### EPrints reference links

+ [Installing EPrints](http://wiki.eprints.org/w/Installation) - basic installation guide
+ [Installing EPrints 3 on Debian](https://wiki.eprints.org/w/Installing_EPrints_3_on_Debian) - legacy docs for Debian/Ubuntu (very stale)

