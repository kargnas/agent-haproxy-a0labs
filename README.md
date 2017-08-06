# Monitoring pluging Haproxy python

This plugin allows you to monitor your HAproxy loadbalancer. You can see the state of your frontend (servers loadbalanced) and backend (HAproxy itself)

### Requirements

- New relic account, find our plugin in the plugin central
- Python 2.7 with the python lib requests installed ( pip install requests // find the library directly into the OS's official repository // build it from the sources : http://www.python-requests.org/)
  - Reports of it working on Python 2.6.6, however your mileage may vary and this is not supported.

### Installation

1. Create the newrelic conf directory if it is not created yet
    ```bash
    mkdir /etc/newrelic
    ```

2. Copy the config file into this directory
    ```bash
    cp agent-a0labs.cfg /etc/newrelic/
    ```

3. If you didn't install pip on your system yet, install it first.
    ```bash
    # In Ubuntu
    apt-get install python-pip
    ```

4. The python `requests` library is required:
    ```
    pip install requests
    ```

### Configuration

Fill the informations in the cfg file:
- License Key
- URL to access the stat CSV Haproxy's file
- user and password
Optional:
- hostname if you want to customize your hostname in newrelic GUI.
- enable/disable logs and specify the directory

### RUN
```
newrelic-haproxy-agent -c haproxy-agent.cfg
```

### Daemonize
There are a few ways to be sure the plugin remains running as a Daemon or service, some are better than others - but each should be selected based on your need.

- supervisord
- use a nohup to launch it in background an detach it when you'll quit the terminal
