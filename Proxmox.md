# Anleitung: Verwendung von VM-Templates auf Proxmox

Diese Anleitung zeigt dir, wie du ein VM-Template von einem Remote-Server herunterlädst, entpackst und auf deinem Proxmox-Server wiederherstellst. Die Pfade und die ID der VM kannst du nach deinen eigenen Bedürfnissen anpassen.

## Voraussetzungen:
- Ein funktionierendes Proxmox-System
- Zugriff auf die Proxmox-Konsole
- Internetverbindung für den Download
- Root-Zugriff oder entsprechende Berechtigungen auf dem Proxmox-Server

---

## Schritt-für-Schritt-Anleitung:

### 1. Wechsle in das Verzeichnis, in dem die Templates/Backups gespeichert werden sollen:

Wähle einen Ordner auf deinem Proxmox-Server, in dem du das Template speichern möchtest. Ein typischer Pfad könnte `/var/lib/vz/dump` sein, aber du kannst auch ein eigenes Verzeichnis wählen.

```bash
cd /pfad/zu/deinem/verzeichnis

wget <url-zum-template>

zstd -d <template-datei>.zst

qmrestore /pfad/zu/deinem/verzeichnis/<template-datei>.vma <vm-id> --storage <storage-name>

sudo rm -r *
