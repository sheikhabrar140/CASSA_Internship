# tart
Transient Array Radio Telescope

##note to contributors
run this command on git bash terminal to leave line endings as they are
```
git config --global core.autocrlf input
```
All the commands on this README.md was run for stimela version 2.0.1.1 and apptainer version 1.4.4<br>


# Installation
This installation method needs WSL 2<br>
You must need WSL2. To check the WSL version clearlt, go to powershell or git bash and type<br>
```
wsl -l -v
```
If it is WSL 2, then proceed to the next step. If ot then, install WSL 2 at first. <br> 
Go to WSL terminal, then <br>
## Installing apptainer globally
```
sudo apt update
wget https://github.com/apptainer/apptainer/releases/download/v1.4.4/apptainer_1.4.4_amd64.deb
wget https://github.com/apptainer/apptainer/releases/download/v1.4.4/apptainer-suid_1.4.4_amd64.deb

sudo apt install -y ./apptainer_1.4.4_amd64.deb
sudo dpkg -i ./apptainer-suid_1.4.4_amd64.deb

apptainer --version
```
## Installing extra runtime dependencies
```
sudo apt install -y squashfuse fuse2fs gocryptfs
```


## Make a dedicated directory and cd into it
```
mkdir pipeline
cd pipeline
```


## Installing tart cargo and stimela into a virtual environment
```
python3 -m venv start
source start/bin/activate
pip install tart_cargo
pip install cult_cargo
pip install stimela

```

## Copy necessary files and folders into your directory
At first, git clone this repo<br>
Then, assuming you have git cloned into D: partition in your Windows<br>
```
cp /mnt/d/tart/tart_dl.yaml .
cp /mnt/d/tart/casacabs.yaml .
cp /mnt/d/tart/make_mov.py .
cp -r /mnt/d/tart/casa/ ./casa/
```

## Check all the steps in the tart_dl.yaml recipe by running this stimela command
```
stimela doc tart_dl.yaml
```

The steps are - <br>
initimgdir<br>
initdatadownloaddir<br>
initdatacaltabledir<br>
initmsdir<br>
download-hdf<br>
create-ms<br>
updateobservatory<br>
flagsave<br>
plotuv<br>
plotants<br>
lister<br>
calibrate_amplitude<br>
plotcaltable_amp<br>
calibrate_phase<br>
plotcaltable_phase<br>
applycal<br>
snapshotimage<br>     
