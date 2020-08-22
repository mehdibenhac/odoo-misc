# 💿 How to install Odoo on Windows

> Copied and modified from: [Odoo 11 Windows Installation](https://github.com/kasim1011/odoo-11.0-windows-installation/blob/master/README.md)

----------
## Odoo 11.0 Windows Installation
Install odoo-11.0 from source on Windows

It is recommended to have 64 bit version of operating system installed on your system.<br />
It is recommended to install 64 bit version of all software packages mentioned in installation process.<br />

### Installation<br />
Download and install [Git for Windows](https://git-scm.com/download/win).<br />
Download and install [Node.js LTS](https://nodejs.org/en/download/).<br />
<br />
Launch `Command Prompt` as Administrator.
 *  **Not sure if necessary, but:** Install `Less.js` by `> npm install -g less less-plugin-clean-css`

Download and install [PostgreSQL](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads).<br />
add PostgreSQL's `bin` directory (default: `C:\Program Files\PostgreSQL\x.x\bin`) to your `PATH`.<br />
<br />
create a `postgres` user with a password using the `PgAdmin` GUI:<br />
 * open `PgAdmin4`,
 * expand `server` node to create a connection,
 * expand `PostgreSQL` node,
 * select **Object-> Create -> Login/Group Role**,
    * enter the username in the `Role Name` field (e.g. odoo),
    * open the `Definition` tab and enter the password (e.g. odoo),
    * open the `Privileges` tab and give `login` and `create database` rights,
 * click `save`.

Download and install [`Microsoft Visual C++ 2015 Redistributable`](https://www.microsoft.com/en-us/download/details.aspx?id=52685) 
> **✅ This installer is no longer available. Refer to this instead and scroll down to the second ANSWER: [How to install Visual C++ Build Tools 14.0](https://stackoverflow.com/questions/48541801/microsoft-visual-c-14-0-is-required-get-it-with-microsoft-visual-c-build-t)**

Download and install <a href="https://www.python.org/downloads/" target="_blank">Python3</a> `version 3.6`.<br />
 * goto `Python3` installation directory (default: `C:\Users\{UserName}\AppData\Local\Programs\Python\PythonXX`.<br />
 * rename `python.exe` to `python3.exe` and `pythonw.exe` to `pythonw3.exe`.<br />
 * add `Python3` installation directory (default: `C:\Users\{UserName}\AppData\Local\Programs\Python\PythonXX`) to your `PATH`.<br />

Some of `odoo` dependencies are `non-pure Python packages` which requires `C/C++` compilation during their installation process. you can install those dependencies using one of the following approaches.
 1. Download and install already compiled dependencies in `Wheel (.whl)` format targeting your system configuration.
 2. Download and install `C/C++` compiler than install those dependencies from `source`.

For installing dependencies from `Wheel (.whl)`, launch `Command Prompt` as Administrator.<br />
 * Install `pypiwin32` by `> python3 -m pip install pypiwin32`
 * Install [`Pillow`](http://www.lfd.uci.edu/~gohlke/pythonlibs/#pillow) by `> python3 -m pip install Pillow-3.4.2-cp36-cp36m-win_amd64.whl`
 * Install [`gevent`](https://pypi.python.org/pypi/gevent) by `> python3 -m pip install gevent-1.2.2-cp36-cp36m-win_amd64.whl`
 * Install [`lxml`](https://pypi.python.org/pypi/lxml) by `> python3 -m pip install lxml-3.8.0-cp36-cp36m-win_amd64.whl`
 * Install [`psutil`](https://pypi.python.org/pypi/psutil) by `> python3 -m pip install psutil-5.3.1-cp36-cp36m-win_amd64.whl`
 * Install [`psycopg2`](https://pypi.python.org/pypi/psycopg2) by `> python3 -m pip install psycopg2-2.7.3-cp36-cp36m-win_amd64.whl`
 * Install [`pyldap`](http://www.lfd.uci.edu/~gohlke/pythonlibs/#pyldap) by `> python3 -m pip install pyldap-2.4.37-cp36-cp36m-win_amd64.whl`
 * Install [`reportlab`](https://pypi.python.org/pypi/reportlab) by `> python3 -m pip install reportlab-3.4.0-cp36-cp36m-win_amd64.whl`

If you're having `32 bit Windows architecture` or other `Python` versions (e.g. `3.4`, `3.5`) installed on your system. you can download `non-pure Python package Wheels (.whl)` targeting your system configurations from [`PyPI`](https://pypi.python.org/pypi) or [`Laboratory for Fluorescence Dynamics`](http://www.lfd.uci.edu/~gohlke/pythonlibs/). If you're having `Python 3.4` installed on system then you will require [`Microsoft Visual C++ 2010 Redistributable`](http://www.microsoft.com/download/en/details.aspx?id=26999) instead of `Microsoft Visual C++ 2015 Redistributable`. for more information visit [`WindowsCompilers`](https://wiki.python.org/moin/WindowsCompilers) article on `Python Wiki`.

For installing dependencies from `source`, download [`Visual C++ 2015 Build Tools`](http://landinghub.visualstudio.com/visual-cpp-build-tools).<br />
 * run the installer,
 * select `custom` mode for installation,
 * uncheck all optional features (e.g. `Windows 8.1 SDK`, `Windows 10 SDK`, `ATL/MFC SDK`, `.NET Framework SDK` etc.)
 * click `Install`.<br />

After `Visual C++ 2015 Build Tools` installation process completes, launch `Command Prompt` as Administrator
 * Install `pypiwin32` by `> python3 -m pip install pypiwin32`
 * Install `Pillow` by `> python3 -m pip install pillow`
 * Install `gevent` by `> python3 -m pip install gevent`
 * Install `lxml` by `> python3 -m pip install lxml`
 * Install `psutil` by `> python3 -m pip install psutil`
 * Install `psycopg2` by `> python3 -m pip install psycopg2`
 * Install `pyldap` by `> python3 -m pip install pyldap` 
 * Install `reportlab` by `> python3 -m pip install reportlab`

> **🔰 If pyldap throws a fatal error during installation, install it using the wheel file available here: [Python Extension Packages for Windows - Christoph Gohlke](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pyldap) scrolldown to pyldap and chose the file according to your python version. If you're running python 3.7, download: `pyldap‑2.4.45‑cp37‑cp37m` and install it using `pip3 install <file.whl>`**

> **🔰 If, when you run `pip3 install -r requirements.txt` you receive errors after this, it is most likely due to conflicting versions. Open up the requirements.txt file and search for the package giving you issues. remove the version beside it. Ex: `reportlab == 3.3.0` becomes `reportlab`**

> **🔰 If you receive an error about reportlab once you're done with the installation and try to run odoo-bin, it means your reportlab package was corrupted. simply run this command to reinstall it: `pip3 install --upgrade --force-reinstall reportlab`**


If you're having `Python 3.4` installed on system then you will require [`Microsoft Windows SDK for Windows 7 and .NET Framework 4`](https://www.microsoft.com/en-us/download/details.aspx?id=8279) instead of `Visual C++ 2015 Build Tools`. for more information visit [`WindowsCompilers`](https://wiki.python.org/moin/WindowsCompilers) article on `Python Wiki`.

Install remaining `pure Python packages` from [`requirements.txt`](https://github.com/kasim1011/odoo-11.0-windows-installation/raw/master/requirements.txt) using
 * `$ python3 -m  pip install -r requirements.txt`
 * `$ python3 -m pip install -U werkzeug`

Download and install [wkhtmltopdf](https://wkhtmltopdf.org/downloads.html).<br />
Add wkhtmltopdf's `bin` directory (default: `C:\Program Files\wkhtmltopdf\bin`) to your `PATH`.<br />
<br />
Launch `Command Prompt`.<br />
Switch to (`cd`) your desired `odoo` installation directory<br />
clone `odoo` repository by `git clone https://github.com/odoo/odoo.git -b 11.0`<br />

Switch to `odoo` installation directory and run `odoo` using<br />
`$ python3 odoo-bin -w odoo -r odoo --addons-path=addons --log-level=debug_rpc`<br />

<img src="https://raw.githubusercontent.com/kasim1011/odoo-11.0-windows-installation/master/Screenshot.png" />
