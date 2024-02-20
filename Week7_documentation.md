# Managing Software

## sudo
sudo command by default executes a command as the superuser
superuser = root
prepend sudo to regular commands (i.e. sudo mkdir data, sudo touch data.csv)

## apt
apt command is used to install, update, and uninstall software
      sudo apt update
- shows what software can be upgraded
      sudo apt upgrade
- upgrades software packages
      apt search
- used to search for package names
      apt show
- shows more information about a package
      sudo apt install *package*
- installs the package listed
      sudo apt remove *package*
- removes the package listed
      sudo apt autoremove
- removes dependencies
      sudo apt clean
- removes extra files and frees up disk space

## Library Search
yaz-client - a tool that serves as a gateway to information retrieval using the Z39.50 protocol
### Installation
      apt search yaz
      apt show yaz
      sudo apt install yaz

### Documentation
      man yaz-client
      man bibl-attr

### Using yaz
      yaz-client
- open yaz
      Z>
- starts a separate command line interface
      open saalck-uky.alma.exlibrisgroup.com:1921/01SAA_UKY
- accesses UKYs OPAC

### Queries
      find @and @attr 1=4 "information" @attr 1=21 "library science"
- find sends a search request
- @and signifies boolean AND
- @attr 1=4 intructs the query to search for the term in the Title
- "information" is the first search term
- @attr 1=21 instructs the query to search for the term in the Subject-heading
- "library science" is the second search term
      show 1
- show command is used to look at results

## Downloading bat
      sudo apt update
      sudo apt upgrade
      apt search bat
      apt show bat
      sudo apt install bat
