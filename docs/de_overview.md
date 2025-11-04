# Übersicht
Das Projekt teilt sich in drei Teile
- [3D Druck](./de_printing.md)
- [Elektronik](./de_electronics.md)
- [Software](./de_software.md)

## Allgemein
Eine gute Übersicht geben folgende Links:
- https://ytec3d.com/glados-lamp/
- https://www.instructables.com/A-fully-3D-printable-GlaDOS-Robotic-ceiling-arm-la/

Darüber hinaus möchte diese Projekt in folgenden Punkten unterstützen:
- Optimierter 3D Druck durch angepasste STL Dateien
- Mikrocontroller Steuerung
- Heimintegration
- Schritt für Schritt Aufbauanleitung

### Architektur
Folgendes Diagramm zum verstehen der Architektur
```mermaid
flowchart LR
GLADOS[Glados]
G_LIGHT[8 LED weiss]
G_EYE[1 LED orange]
G_PIR[3 Bewegungssensoren]
G_RADAR[Abstandssensor]
G_SOUND[MP3 Sound]
G_MOVE[Servo Steuerung]
G_FAN[Lüfter]
G_TEMP[Temperatursensor<br> - geplant]
G_MIC[Microfon<br> - geplant]
MQTT[MQTT Broker]
NR[NodeRed]
NR_UI[Website]
CLIENT[Handy]
HA[Home Automation]
subgraph Lampe
GLADOS-.->G_LIGHT
GLADOS-.->G_EYE
GLADOS-.->G_PIR
GLADOS-.->G_RADAR
GLADOS-.->G_SOUND
GLADOS-.->G_MOVE
GLADOS-.->G_FAN
GLADOS-.->G_TEMP
GLADOS-.->G_MIC
end
subgraph docker
GLADOS--->|WiFi|MQTT
MQTT-->NR
NR-->NR_UI
end
HA-->MQTT
NR_UI-->CLIENT
```