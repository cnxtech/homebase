# tracts


A place for your app to call home.

*tracts* provides a platform independent API for querying paths where applications can write caches, data, configs, and
other information.


## rationale 

Since each operating system expects applications to write their data to OS dependant paths, managing cache writing
on portable applications can become difficult.

For example, on macOS:

    ~/Library/Application Support/app_name

while on Linux it may be:

    ~/.local/share/app_name
    
and on Windows:
    
    c:\users\<user_name>\AppData\Local/app_name

and the problem gets worse if you are running inside of a [virtualenv](https://virtualenv.pypa.io/en/stable/)

A similar issue happens for other forms of data, like caches, logs, configuration files, or application state.

## Installation

```bash
python setup.py install
```


## Usage

```python
import tracts

app_name = "my_app"
user_data_dir = tracts.user_data_dir(app_name=app_name)
user_cache_dir = tracts.user_cache_dir(app_name=app_name)
user_logs_dir = tracts.user_log_dir(app_name=app_name)
user_config_dir = tracts.user_config_dir(app_name=app_name)
user_state_dir = tracts.user_state_dir(app_name=app_name)

# site specific directories, e.g. /usr/share
site_data_dirs = tracts.site_data_dirs(app_name=app_name)
site_config_dirs = tracts.site_condig_dirs(app_name=app_name)
```

If you are running inside of a virtualenv, *tracts* will return paths that are relative to that environment.
If you still want the user path, pass `use_virtualenv=False` in the call.

```python
import tracts

app_name = "my_app"
user_data_dir = tracts.user_data_dir(app_name=app_name, use_virtualenv=False)
```

See the [documentation](# TODO) for more details and examples.

## License

See [LICENSE.txt](LICENSE.txt)


## Acknowledgement

This project is inspired by and is derived from [appdirs](https://github.com/ActiveState/appdirs)
