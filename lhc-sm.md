# LHC Signal Monitoring

This is a gallery of example notebooks about LHC Signal Monitoring project (https://cern.ch/sigmon).

[<img class="open_in_swan" data-path="lhc" alt="Open this Gallery in SWAN" src="https://swanserver.web.cern.ch/swanserver/images/badge_swan_white_150.png">][gallery_url]

<img src="https://gitlab.cern.ch/LHCData/lhc-sm-api/raw/master/figures/logo.png" width=25%>

The Signal Monitoring project architecture consists of four elements:

1. API for logging db query and signal processing (<a href="https://gitlab.cern.ch/lhcdata/lhc-sm-api">https://gitlab.cern.ch/lhcdata/lhc-sm-api</a>) 
2. Signal Monitoring notebooks (<a href="https://gitlab.cern.ch/lhcdata/lhc-sm-apps">https://gitlab.cern.ch/lhcdata/lhc-sm-apps</a>)
3. HWC and Operation notebooks (<a href="https://gitlab.cern.ch/lhcdata/lhc-sm-hwc">https://gitlab.cern.ch/lhcdata/lhc-sm-hwc</a>)
4. Scheduler for execution of HWC notebooks and monitoring applications (<a href="https://gitlab.cern.ch/lhcdata/lhc-sm-scheduler">https://gitlab.cern.ch/lhcdata/lhc-sm-scheduler</a>)
<img src="https://gitlab.cern.ch/LHCData/lhc-sm-api/raw/master/figures/lhc-sm-architecture.png" width=50%>

## Signal Monitoring API Architecture


The API is a collection of six modules for:  
- database access (DBSignal); 
- signal, system, circuit naming (Metadata); 
- signal and event references (Reference); 
- embedded domain specific language for signal/feature/event query and processing, signal assertion, and feature engineering;
- signal query, analysis, and plot (Analysis); 
- graphical user interfaces for browsing of historicalsignal features (GUI).

<img src="https://gitlab.cern.ch/LHCData/lhc-sm-api/raw/master/figures/lhc-sm-api-architecture.png" width=50%>

## Installation
There are two ways of using the API in your code:

1. Loading pre-installed packages from an EOS project folder (in SWAN environment)
2. Manual installation (in any environment)

The first option guarantees the use of the most recent code version without manual installation. The second one is more time consuming, however, works in environments with no access to the EOS folder (e.g., Apache Airflow scheduler). In addition, the second method allows to install a selected version (`pip install package_name=version`).

### Preinstalled Packages
To use the set of pre-installed packages please follow these three steps:

1. Contact the Signal Monitoring team (mailto:lhc-signal-monitoring@cern.ch) in order to get read access to the EOS folder with pre-installed packages.
2. (optional) Uninstall existing packages.  
Initially, the packages were installed manually as discussed in Section Manual Installation. Depending on the settings, a python script (or notebook) might use manually installed packages instead of the pre-installed ones.
Thus, to avoid issues related to a double reference to a package, please uninstall (with `pip uninstall package_name`) all packages required by the API (tzlocal, tqdm, influxdb, plotly, lhcsmapi). 
This operation has to be done only once provided that the packages were installed (to check if a package was installed use `pip list | grep package_name` in SWAN Command Line Interface).
3. While logging to SWAN service, please add the environment script as `/eos/project/l/lhcsm/public/packages.sh`
<img src="https://gitlab.cern.ch/LHCData/lhc-sm-api/raw/master/figures/swan_environment_script.png" width=50%>

### Manual Installation
In order to use the API, it has to be installed with a python package installer as

```python
pip install --user lhcsmapi
```
Check the latest version at <a href="https://pypi.org/project/lhcsmapi/">https://pypi.org/project/lhcsmapi/</a>

The API relies on several external python packages which have to be installed in a similar manner. The list of packages is stored in the <u><i>requirements.txt</i></u> file.

If you use SWAN, the service provides a set of pre-installed python packages through CVMFS. The LHC-SM notebooks require installation of several additional packages on top of CVMFS. In order to install a package, please open a SWAN Terminal by clicking [>_] icon in the top right corner.

![SWAN CLI Button](https://gitlab.cern.ch/LHCData/lhc-sm-hwc/-/raw/master/figures/swan-cli-button.png)

Five additional python packages have to be installed:
- tzlocal - for time zone convertion
- tqdm - for progress bar to track queries
- influxdb - for communication with an Influxdb
- plotly - for interactive plotting of circuit schematics 
- lhcsmapi - for LHC-SM API
In order to install a package please execute the following command
```
$ pip install --user package_name
```


[gallery_url]:https://cern.ch/swanserver/cgi-bin/go/?projurl=http://gitlab.cern.ch/lhcdata/lhc-sm-api.git
