
# Fragekatalog: 9. Januar 2025

## 1. IP: Funktion, Strukturen, Methoden, Prozesse

### 1.1 Welche Funktion(en) erfüllt das IP-Protokoll?
- **Hauptfunktion:** Zustellung von Paketen über ein Netzwerk hinweg, unabhängig von der zugrunde liegenden Hardware.
- **Adressierung:** Zuweisung von eindeutigen IP-Adressen, um Sender und Empfänger eindeutig zu identifizieren.
- **Fragmentierung:** Zerlegung von Daten in kleinere Pakete, die über das Netzwerk transportiert werden können.
- **Routenfindung:** Bestimmung des optimalen Pfades für die Pakete.

### 1.2 Welche IP-spezifische Struktur(en) werden verwendet?
- **IP-Header:** Struktur, die wichtige Felder wie Version, Header Length, Total Length, Source Address, Destination Address, Time-to-Live (TTL), und Protokollnummer enthält.
- **IP-Adressen:** Struktur aus Netzanteil und Hostanteil, meist im IPv4- oder IPv6-Format.

### 1.3 IP-Adresse: Funktion des Feldes `length`?
- **Feld `Total Length`:** Gibt die Gesamtlänge des IP-Pakets an (Header + Nutzdaten).
  - Ermöglicht es, die Größe des Pakets zu kennen, was für die Fragmentierung und die Verarbeitung durch Router und Empfänger wichtig ist.

### 1.4 Was ist ein Interface und welche Beziehung(en) besteht zwischen Interface und IP-Protokoll?
- **Interface:** Eine Schnittstelle, die es einem Gerät ermöglicht, mit einem Netzwerk zu kommunizieren (z. B. Ethernet, WLAN).
- **Beziehung:** Das IP-Protokoll wird auf einem Interface implementiert, das eine eindeutige IP-Adresse erhält. Ein Gerät kann mehrere Interfaces mit unterschiedlichen IP-Adressen haben.

### 1.5 Mit welchem Befehl kann ich die IP-Adresse meines Hosts feststellen?
- **Linux/macOS:** `ip addr` oder `ifconfig`
- **Windows:** `ipconfig`

### 1.6 Struktur einer IP-Adresse: Was sind die relevanten Terme/Konzepte und wo (wofür) werden diese gebraucht?
- **IPv4-Adresse:** 32 Bit, aufgeteilt in Netzanteil und Hostanteil.
- **IPv6-Adresse:** 128 Bit, für größere Adressräume.
- **Subnetzmaske:** Bestimmt den Netzanteil einer IP-Adresse.
- **CIDR (Classless Inter-Domain Routing):** Notation, z. B. `192.168.1.1/24`, die Netzwerke effizienter adressiert.
- **Gateway:** Adresse des Routers, der Daten in andere Netzwerke weiterleitet.
- **DNS (Domain Name System):** Übersetzt Hostnamen in IP-Adressen.

---

## 2. TCP/UDP: Funktion, Strukturen, Methoden, Prozesse

### 2.1 Welchen Service/Funktion erfüllt das UDP-Protokoll?
- **Hauptfunktion:** Verbindungsloser Transport von Daten zwischen Sender und Empfänger.
  - Keine Garantie für die Zustellung.
  - Schneller und effizienter, z. B. für Echtzeitanwendungen wie VoIP oder Video-Streaming.

### 2.2 Welchen Service/Funktion erfüllt das TCP-Protokoll?
- **Hauptfunktion:** Verbindungsorientierter Transport von Daten.
  - Zuverlässige Zustellung durch Bestätigungen (ACK).
  - Reihenfolgeerhaltung und Fehlerkontrolle.
  - Anwendungsbeispiele: HTTP, FTP, E-Mail.

### 2.3 Mit welchem Befehl kann ich feststellen, ob ein Port offen ist?
- **Linux/macOS:** `netstat -an` oder `ss -tuln`
- **Windows:** `netstat -an`
- **Port-Scan-Tools:** `nmap <IP-Adresse>` oder `telnet <IP-Adresse> <Port>`

### 2.4 Welche Ports sind für bestimmte Protokolle reserviert?
- **Well-Known Ports (0–1023):**
  - HTTP: Port 80
  - HTTPS: Port 443
  - FTP: Port 21
  - SSH: Port 22
  - DNS: Port 53
- **Registered Ports (1024–49151):** Für spezifische Anwendungen.
- **Dynamic/Private Ports (49152–65535):** Für temporäre Verbindungen.

---

## 3. TCP Tunnel: Port Forwarding mit SSH

### Wie kann mit SSH ein Tunnel zwischen `host1:port1` und `host2:port2` erstellt werden?

1. **Syntax:**
   ```bash
   ssh -L [lokaler_Port]:[Zielhost]:[Zielport] [Benutzer]@[SSH-Server]
   ```
   Beispiel:
   ```bash
   ssh -L 8080:host2:80 user@host1
   ```
   - Leitet den lokalen Port `8080` an `host2` Port `80` über `host1` weiter.

2. **Mit `netcat` testen:**
   - Verbindung testen:
     ```bash
     nc -zv localhost 8080
     ```
   - Erfolgreiche Verbindung zeigt, dass der Tunnel funktioniert.

---
