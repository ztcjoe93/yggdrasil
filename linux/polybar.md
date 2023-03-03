Last updated: 2023-03-04 12:41

## Setting up multi-monitors

```sh
for m in $(polybar --list-monitors | cut -d":" -f1); do
    MONITOR=$m polybar --reload example &
done
```
Configured within a shell script -- checks for monitors listed dynamically by polybar, and does a delimiter split + retrieve 1st argument.  

```sh
[bar/main]
monitor=${env:MONITOR:}
```
In your polybar configuration  

The setup effectively launches polybar for the respective monitor-port stored in the `MONITOR` env var.  
```shell
for m in $(polybar --list-monitors | cut -d":" -f1); do
	MONITOR=$m polybar -q main -c "$dir/$style/config.ini" &
done
```
_example to integrate multi-monitor with polybar-themes_  

