## Workflow

docker compose up -d

Beim Starten werden alle benötigten Images bei Bedarf aus dem Internet geladen und gestartet

Influx wird mit Benutzer/Passwort 'admin/admin123' eingerichtet; Authorization-Token wird zugewiesen. Organisation: 'WST'; Datenbank(Bucket): 'WST-Bucket'

Grafana wird mit Benutzer/Passwort 'admin/admin123' eingerichtet; Dashboard 'WST-Graf22'; Datasource "Influx_WST" (Authorization-Token)

nachdem docker compose up -d ausgeführt wurde kann mit Hilfe von 'curl' Testdaten zum 'telegraf'-Container geschickt werden.

sudo curl -i -XPOST 'http://telegraf:8086/api/v2/write?org=WST&bucket=WST-Bucket' --data-binary 'airSennsors,sensor_id=TLM201 temperature=80,humidity=38,co=0.44'

sudo curl -i -XPOST 'http://telegraf:8086/api/v2/write?org=WST&bucket=WST-Bucket' --data-binary 'airSennsors,sensor_id=TLM201 temperature=90,humidity=48,co=0.74'

Grafana: localhost:3000

InfluxDB: localhost:8086

Telegraf wurde kein Port zugewiesen

## getestet unter 
- Windows 10 mit Docker Desktop
- Linux VM Debian 12 mit Desktop
