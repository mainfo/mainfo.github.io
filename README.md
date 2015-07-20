# mine info

## Export the blurry coordinates to a geojson

Connect to the server in SSH
```
mkdir mapps
cd mapps
```
To install the mysql librairy :

```
sudo apt-get install libmysqlclient-dev
sudo apt-get install python-mysqldb
```

Create the data folder
```
mkdir data
```

Create the python file
```
touch usha_get_loc.py
```
Enter the file and copy paste the script
```
nano usha_get_loc.py
```
Paste, replace the missing connexion strings by yours.
CTRL X / yes and Enter to save

Create the publicmap repo
```
cd /var/www/
sudo mkdir publicmap
sudo chown cartong publicmap
```
Create a folder map

```
cd publicmap
sudo mkdir map
sudo chown cartong map
```
Go back to the mapps folder
```
cd /home/cartong/mapps/
```
And run the script
```
python usha_get_loc.py
```
And it should have created a data.json file in the data folder and in the /var/www/publicmap/map/ folder

Yeah :)

## Run the script every hour

```
crontab -e
```
At the end paste the line:
```
 0 * * * * python /home/cartong/mapps/usha_get_loc.py > ~/robo-heat.log 2>&1
```
It will run the script every first minute of every hour and it will create a log file

Yeah :)

## The heatmap
