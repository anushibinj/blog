# Convert MKV to MP4 from CMD
```sh
ffmpeg -i LostInTranslation.mkv -codec copy LostInTranslation.mp4
```

# Convert Video to MP3

```sh
ffmpeg -i sample.avi -q:a 0 -map a sample.mp3
```

# Bulk cleanup videos (just copy the stream with audio conversion to AAC - for CCTV videos)
```sh
for /r %%v in (*.mp4) do ffmpeg -y -i "%%v" -acodec aac -vcodec copy "%%v.mp4"
```

# Mount an ISO from CMD
```powershell
PowerShell Mount-DiskImage
```

# Install SSHD
```sh
powershell.exe -ExecutionPolicy Bypass -File install-sshd.ps1
```

# Show seconds in taskbar clock
```regedit
REG ADD HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced /t REG_DWORD /v ShowSecondsInSystemClock /d 1 /f
```

# Python HTTP Server
```sh
python -m SimpleHTTPServer
```
```sh
python3 -m http.server
```

# Search inside JAR using 7 Zip
```
7z l archive_name.extension file_name.extension -r
```

# Docker WatchTower
```sh
docker run --detach --name watchtower -e WATCHTOWER_NO_PULL=true -e WATCHTOWER_POLL_INTERVAL=5 --volume /var/run/docker.sock:/var/run/docker.sock containrrr/watchtower
```

# Add delay in JS
```javascript
const delay = (time) => {
	return new Promise(function (resolve) {
		console.log(`Waiting ${time} millis...`);
		setTimeout(resolve, time);
	});
};
```

# Prune remote and local branches in Git

```sh
git fetch -p
npx git-removed-branches --prune
```

# Windows 10 Context Menu in Windows 11

```sh
reg.exe add "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /f /ve
```

# Commit git repo with custom commit author

```
[user]
	email = anushibin007@gmail.com
	name = Anu Shibin Joseph Raj
```
# Run Spring Boot App with dev profile

```sh
mvn spring-boot:run -Dspring.profiles.active=dev
```

# Watch command in Windows

```bat
@ECHO OFF
:loop
  cls
  %*
  timeout /t 5 > NUL
goto loop
```

# pip to uv migration

```bat
uv init --bare
uv add -r requirements.txt
```

# Install node_exporter for Prometheus

```sh
sudo useradd --no-create-home --shell /bin/false node_exporter
cd /tmp/
wget https://github.com/prometheus/node_exporter/releases/download/v1.12.1/node_exporter-1.12.1.linux-amd64.tar.gz
tar xvf node_exporter-1.12.1.linux-amd64.tar.gz
cp node_exporter-1.12.1.linux-amd64/node_exporter /usr/local/bin/
chown node_exporter:node_exporter /usr/local/bin/node_exporter
vim /etc/systemd/system/node_exporter.service
```

```
[Unit]
Description=Prometheus Node Exporter
After=network.target

[Service]
User=node_exporter
Group=node_exporter
Type=simple
ExecStart=/usr/local/bin/node_exporter

[Install]
WantedBy=multi-user.target
```

```
sudo systemctl daemon-reload
sudo systemctl enable --now node_exporter
sudo systemctl status node_exporter
curl http://localhost:9100/metrics
```
