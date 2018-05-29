MITIE-PHP
---------

**STATUS**

In development/unstable. 

MITIENer() class is now functional for named entity extraction (see demo MITIE.php file). 

**ABOUT**

A PHP 5 extension based on PHP-CPP that wraps the excellent MITIE (MIT Information Extraction) library https://github.com/mit-nlp/MITIE

It currently allows you to perform named entitiy extraction within your PHP scripts (other classes and functions to be added). 

**INSTALLATION**

There are no pre-compiled binaries (yet), so you will need to compile from source. The installation instructions below are relevant for a Debian/Ubuntu box.

The library is based on PHP-CPP, so first you need to install php-dev:

```
sudo apt-get install php5-dev
``` 
or 

```
sudo apt-get install php5.6-dev
```
(depending on which version of PHP5 you have installed).

Download and install the PHP-CPP-LEGACY library by following the instructions here:
https://github.com/CopernicaMarketingSoftware/PHP-CPP-LEGACY/blob/master/documentation/install.html

Clone the MITIE-PHP repo:

```
git clone https://github.com/rjjakes/MITIE-PHP.git
```

And pull down the MITIE library which is referenced as a git submodule:

```
git pull --recurse-submodules
```

Compiling MITIE as a shared library : (see https://github.com/mit-nlp/MITIE#compiling-mitie-as-a-shared-library)


```
cd MITIE/mitielib
make
```

Edit these two lines in the Makefile so the config and ini directories point to your local directories (in the example below, I have PHP5.6 installed and will be attaching the library to the command line interface instance of PHP).
 
```
PHP_INI_DIR	    = /etc/php/5.6/mods-available/
```

```
PHP_CONFIG_DIR	= /etc/php/5.6/cli/conf.d/
```


Now build the project:

```
make && sudo make install
```

**USAGE**

For named entity extraction/named entity recognition

```
$ner = new MITIENer();
$ner->loadModel("MITIE/MITIE-models/english/ner_model.dat");
$ner->extraction("MITIE/sample_text.txt");
$entities = $ner->getEntities();
```


