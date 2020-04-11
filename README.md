## Structure 
```bash
mkdir -p $HOME/crontab.d
mkdir -p $HOME/crontab.d/system
mkdir -p $HOME/crontab.d/apache2

touch $HOME/crontab.d/system.cron
touch $HOME/crontab.d/system/alpha.sh
touch $HOME/crontab.d/system/beta.sh

touch $HOME/crontab.d/apache2.cron
touch $HOME/crontab.d/apache2/stop.sh
touch $HOME/crontab.d/apache2/start.sh

find $HOME/crontab.d -type d -exec chmod 700 {} \;
find $HOME/crontab.d -type f -exec chmod 600 {} \;
```

## Cron files

#### `$HOME/crontab.d/system.cron`
```bash
*/1 * * * * /bin/bash $HOME/crontab.d/system/log.sh >> $HOME/crontab.d/system/log.log 2>&1
*/1 * * * * /bin/bash $HOME/crontab.d/system/test.sh >> $HOME/crontab.d/system/test.log 2>&1
```

#### `$HOME/crontab.d/apache2.cron`
```
30 1 * * * /bin/bash $HOME/crontab.d/apache2/stop.sh > $HOME/crontab.d/apache2/stop.log 2>&1
31 1 * * * /bin/bash $HOME/crontab.d/apache2/start.sh > $HOME/crontab.d/apache2/start.log 2>&1
```

## Install 

```bash
cat $HOME/crontab.d/*.cron | crontab -
```
