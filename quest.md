## Hinweise

Dieser Test enthält 30 Komplexe multiple-choice  Fragen:

- 10 — Networking
- 10 — Windows / Active Directory
- 10 — Linux, 

- Wähle **alle Antworten aus, die Sie für korrekt halten**.
- Es kann **keine, eine oder mehrere korrekte Antworten** sein.
- Beurteile ausschließlich die Informationen, die in der jeweiligen Aufgabe gegeben werden.
- Bei Konfigurationen oder Command-Outputs: Achten sie auf die Unterschiede zwischen dem, was die vorliegenden Daten **belegen**, und dem, was **vermutet** wird.

---

# Teil I — Networking

## Frage 1 — IPv4-Grundlagen

Ein APC hat folgende Konfiguration:

```
IP-Adresse:       192.168.10.25
Subnetzmaske:     255.255.255.0
Default Gateway:  192.168.10.1
```

Welche Aussagen sind korrekt?

A. `192.168.10.25` und `192.168.10.1` befinden sich im selben IPv4-Subnetz.

B. Der Arbeitsplatzrechner kann ARP verwenden, um die MAC-Adresse von `192.168.10.1` zu ermitteln.

C. Der Arbeitsplatzrechner wird Datenverkehr zu `192.168.20.25` normalerweise direkt an die MAC-Adresse dieses Hosts senden.

D. Das Default Gateway wird normalerweise verwendet, wenn sich das Ziel außerhalb des lokalen Subnetzes befindet.

E. Das Subnetz enthält exakt 256 nutzbare Host-Adressen.

---

## Frage 2 — Switching

Ein Switch-Port ist folgendermaßen konfiguriert:

```
interface GigabitEthernet1/0/10
 switchport mode access
 switchport access vlan 20
```

Welche Aussagen sind korrekt?

A. Der Port ist als Access-Port konfiguriert.

B. Nicht getaggte Frames, die an diesem Port empfangen werden, werden VLAN 20 zugeordnet.

C. Die Konfiguration stellt sicher, dass nur ein physisches Gerät den Port verwenden kann.

D. Die Konfiguration authentifiziert das angeschlossene Gerät.

E. Die Konfiguration zeigt, dass VLAN 20 das IP-Subnetz `192.168.20.0/24` verwendet.

---

## Frage 3 — Administrativer Status

Ein Administrator sagt:

> „Das Interface hat eine IP-Adresse, daher kann darüber geroutet werden .“

CLI Ausgabe:

```
interface GigabitEthernet1/0/24
 ip address 10.10.20.1 255.255.255.0
 shutdown
```

Welche Aussagen sind korrekt?

A. Das Interface ist aktuell auf Layer 3 betriebsbereit.

B. Das Interface ist aktuell administrativ deaktiviert.

C. Die IP-Adresse ist irrelevant, weil das Interface abgeschaltet ist.

D. Das Interface kann aktuell Pakete weiterleiten.

E. Die Konfiguration zeigt, dass das physische Kabel angeschlossen ist.

---

## Frage 4 — CDP vs. LLDP

Sie auditieren ein Netzwerk mit Geräten von verschiedener Herstellern.
Die Dokumentationen weisen Zwei ähnliche Kommandos auf.
Ein Kamerad Zeigt ihnen folgende Zeilen.

```
show cdp neighbors
show lldp neighbors
```

Welche Aussagen sind technisch korrekt?


A. CDP ist ein herstellerneutrales, standardisiertes Neighbor-Discovery-Protokoll.

B. CDP und LLDP sind dasselbe Protokoll und unterscheiden sich lediglich durch die Bezeichnung des jeweiligen Commands.

C. Die von CDP und LLDP bereitgestellten Informationen können sich abhängig von Gerät und Implementierung unterscheiden.

D. LLDP ist ein Layer-3-Routing-Protokoll.


---

## Frage 5 — ARP

Ein Arbeitsplatzrechner muss mit folgendem Host kommunizieren:

```
10.20.30.50
```

Sie lassen sie die laufenden Konfiguration anzeigen:

```bash
└─$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00                                   
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:0c:29:a8:9b:a5 brd ff:ff:ff:ff:ff:ff                                      
    inet 10.20.10.25/24 brd 10.20.10.255 scope global eth0      
       valid_lft forever preferred_lft forever
    inet6 fe80::4d09:36c3:72b3:590a/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
└─$ ip r
default via 10.20.10.1 dev eth0 proto static metric 100 10.20.10.0/24 dev eth0 proto kernel scope link src 10.20.10.25 metric 100

```

Welche Aussagen sind korrekt?

A. Das Ziel befindet sich außerhalb des lokalen Subnetzes.

B. Der Arbeitsplatzrechner wird normalerweise nach der MAC-Adresse von `10.20.30.50` per ARP suchen.

C. Der Arbeitsplatzrechner benötigt normalerweise die MAC-Adresse seines Default Gateways.

D. Der erste Ethernet-Frame auf dem Weg zum entfernten Netzwerk verwendet normalerweise die MAC-Adresse des entfernten Servers.

E. Um das Zielnetzwerk zu erreichen, wird Routing benötigt.

---

## Frage 6 — VLAN Trunk

Sie lesen folgende CLI Ausgabe an einem Switch:

```
interface Gi1/0/48
 description Uplink-to-SW02
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30
```

Welche Aussagen sind korrekt?

A. Die Konfiguration zeigt, dass drei VLANs aktuell verwendet werden.

B. Die VLANs 10, 20 und 30 sind explizit erlaubt.

C. Native VLAN ist impliziert erlaubt.

D. Die Konfiguration beweist, dass der Datenverkehr dieser VLANs verschlüsselt ist.

E. Das Interface ist als Trunk konfiguriert.

---

## Frage 7 — Routing

Ein Router enthält folgende Einträge:

```
10.0.0.0/8       via 192.168.1.1
10.20.0.0/16     via 192.168.2.1
10.20.30.0/24    via 192.168.3.1
0.0.0.0/0        via 192.168.4.1
```

Ein Paket soll an folgendes Ziel gesendet werden:

```
10.20.30.55
```

Welche Aussagen sind korrekt?

A. Die `/24`-Route ist die spezifischste passende Route.

B. Das Paket wird normalerweise `192.168.3.1` als Next Hop verwenden.

C. Die Default Route wird ausgewählt.

D. Die `/8`-Route wird ausgewählt, weil sie zuerst konfiguriert wurde.

E. Das Ziel passt auf alle drei angezeigten privaten Netzwerk-Routen.

---

## Frage 8 — ACL-Interpretation

Sie finden:

```
ip access-list extended SERVER-IN
 permit tcp 10.10.0.0 0.0.255.255 any eq 443
 permit tcp 10.10.0.0 0.0.255.255 any eq 22
 deny ip any any log
```

Welche Aussagen sind korrekt?

A. TCP/443 aus `10.10.0.0/16` ist erlaubt.

B. Datenverkehr, der die letzte Regel erreicht, wird protokolliert.

C. UDP/53 aus `10.10.0.0/16` ist erlaubt.

D. IP-Datenverkehr, der die letzte Regel erreicht, wird abgelehnt.

E. TCP/22 aus `10.10.0.0/16` ist nicht erlaubt. 

F. Der gesamte Datenverkehr aus `10.10.0.0/16` ist erlaubt.

---

## Frage 9 — Neighbor Discovery und Topologie

Sie untersuchst eine Umgebung mit mehreren Herstellern.

Welche Informationsquellen können bei der Rekonstruktion der Netzwerktopologie hilfreich sein?

A. CDP

B. LLDP

C. MAC-Address-Tables

D. ARP-Tables

E. OSPF-Nachbarschaftsinformationen

F. BGP-Routing-Tabellen

---

## Frage 10 — Network Security Architecture

Ein Unternehmen behauptet:

> „Unser Netzwerk ist segmentiert, weil Benutzer, Server und Management in separaten VLANs liegen.“

Sie stellst folgende Kommunikation fest:

```
User VLAN       → Server VLAN       ALLOW
User VLAN       → Management VLAN   SSH/HTTPS
Server VLAN     → User VLAN         ALLOW
IoT VLAN        → Server VLAN       ALLOW
Management VLAN → All VLANs         ALLOW
```

Welche Aussagen sind angemessen?

A. Die Trennung durch VLANs allein stellt keine effektive Security Boundary dar.

B. Der Zugriff von Benutzer-Systemen auf Management-Systeme sollte untersucht werden.

C. Die Kommunikation vom IoT-VLAN zu Servern sollte anhand einer expliziten fachlichen Anforderung bewertet werden.

D. Die Existenz der VLANs zeigt, dass laterale Bewegungen zwischen diesen Netzwerken verhindert werden.

E. Die erlaubten Kommunikationswege sollten mit dem vorgesehenen Trust Model verglichen werden.

F. Die Kommunikation vom Management-VLAN zu allen anderen VLANs ist automatisch unsicher und muss immer entfernt werden.

---

# Teil II — Windows / Active Directory

## Frage 11 — Active Directory Grundlagen

Welche Aussagen sind korrekt?

A. Active Directory Domain Services stellt zentrale Directory Services bereit.

B. Domain Controller stellen typischerweise Authentication Services für die Domäne bereit.

C. DNS ist für den normalen Betrieb von Active Directory wichtig.

D. Active Directory ersetzt DNS in einer typischen Windows-Domäne.

E. Das Passwort jedes Domain Users wird lokal auf jedem Domain-joined APC gespeichert.

---

## Frage 12 — PowerShell AD Query



Ein Administrator sagt:

„Dieser Computer ist in die Domäne eingebunden, daher wird das lokale Administrator-Konto über das Active Directory gesteuert.“

Sie überprüfen den Computer und stellen fest:
```
PS C:\Users\Bellisarus> systeminfo | Where-object {$_ -like "Dom*"}

Domain:   WORKGROUP

PS C:\Users\Bellisarus> Get-LocalUser

Name                Enabled Description
----                ------- -----------
Administrator       True   Vordefiniertes Konto für die Verwaltung des Computers bzw. der Domäne
Bellisarus          True
```

Welche Aussagen sind  korrekt?

A. Das Konto ist ein Active Directory-Konto.

B. Das Passwort des Kontos ist auf einem Domain Controller gespeichert.

C. Das Konto ist Mitglied der Domänen-Admins.

D. Domänen-Gruppenrichtlinien können das lokale Konto nicht beeinflussen.

E. Das Konto muss sich gegenüber einem Domain Controller authentifizieren.



---

## Frage 13 — Windows Services

Sie führen folgenden Befehl in PowerShell aus:

```
Get-Service |
    Where-Object {$_.Status -eq "Running"}
```

Welche Aussagen sind korrekt?

A. Der Befehl liefert Services, deren gemeldeter Status `Running` ist.

B. Der Befehl beweist, dass jeder angezeigte Service automatisch beim Booten gestartet wird.

C. Der Befehl kann zur Erstellung eines Service-Inventars verwendet werden.

D. Der Befehl verändert die Service-Konfiguration.


---

## Frage 14 — Windows Firewall

Welche Aussagen sind korrekt?

A. Die Windows Defender Firewall kann Netzwerkverkehr anhand von Eigenschaften wie Richtung, Protokoll und Port kontrollieren.

B. Eine Perimeter-Firewall sorgt dafür das eine Host-basierte Firewall-Kontrollen obsolet werden.

C. Die Existenz einer Firewall-Regel beweist nicht, dass diese Regel aktiviert ist.

D. Host-basierte Firewall-Regeln können zusätzlichen Schutz gegen internen Netzwerkverkehr bieten.

---

## Frage 15 — Kerberos

Welche Aussagen sind korrekt?

A. Kerberos verwendet Tickets für Authentication und Service Access.

B. Ein Ticket Granting Ticket kann verwendet werden, um Service Tickets zu erhalten.

C. Eine korrekte Zeitsynchronisation ist für Kerberos wichtig.

D. Kerberos verhindert, dass NTLM-downgrade Angriffe in einer Active-Directory-Umgebung verwendet werden kann.

E. Service Principal Names sind für die Identifikation von Kerberos-Services nicht relevant.

---

## Frage 16 — Group Policy

Welche Aussagen sind korrekt?

A. Group Policy Objects können verwendet werden, um Windows Security Settings zentral zu konfigurieren.

B. Mehrere GPOs können die abschließende resultierende Konfiguration beeinflussen.

C. Die Verknüpfung mit einer GPOs beweist, dass darin enthaltene Einstellungen aktiv sind.

D. Reihenfolge und Vererbung bei der Group-Policy-Verarbeitung können die resultierende Konfiguration beeinflussen.


---

## Frage 17 — Windows Security Logging


Ein Administrator sagt:  
„Ich habe Credential Guard per Gruppenrichtlinie auf allen Windows 11 Clients erzwungen. Damit können unter keinen Umständen mehr Anmeldedaten ausgelesen werden.“

Sie führen auf einem dieser Clients ein Sicherheits-Audit durch und rufen die Systeminformationen auf:

text

```
PS C:\> (Get-CimInstance -ClassName Win32_DeviceGuard -Namespace root\Microsoft\Windows\DeviceGuard).SecurityServicesRunning

1
```

Welche Aussagen sind **korrekt**?

- **A.** Credential Guard läuft ordnungsgemäß und schützt den LSASS-Prozess vollumfänglich.
- **B.** Die Richtlinie greift nicht oder die Hardware liefert keine Untersützung, wodurch LSASS weiterhin anfällig für Credential Dumping ist. 
- **C.** Wert 1 zeigt an, dass Credential Guard im „Legacy-Modus“ läuft, welcher den gleichen Schutz bietet.
- **D.** Der Befehl zeigt nur den Status der Windows Firewall an und hat keine Aussagekraft über LSASS.



---

## Frage 18 — SMB Configuration

Sie führen aus:

```
Get-SmbServerConfiguration |
    Select EnableSMB1Protocol,
           EnableSecuritySignature,
           RequireSecuritySignature
```

Das Ergebnis lautet:

```
EnableSMB1Protocol       : True
EnableSecuritySignature  : False
RequireSecuritySignature : False
```

Welche Aussagen sind korrekt?

A. SMBv1 ist aktiviert.

B. SMB Signing ist zwingend vorgeschrieben.

C. SMB Signing ist gemäß der angezeigten Einstellung nicht als verpflichtend konfiguriert.

D. SMBv1 sollte als potenzielles Hardening-Thema untersucht werden.

E. Die Ausgabe beweist, dass SMB-Datenverkehr unverschlüsselt ist.

---

## Frage 19 — Active Directory und LDAP

Welche Aussagen sind korrekt?

A. Active Directory Domain Services stellt LDAP-Schnittstellen bereit.

B. LDAP ist die vollständige Active-Directory-Authentication-Implementierung von Microsoft .

C. Active Directory verwendet mehrere Protokolle und Services, darunter LDAP, Kerberos und DNS.

D. OpenLDAP und Active Directory bieten exakt dieselbe Windows-Domain-Funktionalität.

E. Eine Anwendung kann LDAP verwenden, um AD abzufragen, ohne dass bei dieser konkreten Operation zwingend Kerberos verwendet wird.

F. OpenLDAP stellt Directory Services bereit, bildet aber nicht automatisch das vollständige AD-Domain-Service-Ökosystem ab.

---
## Frage (19)

---

## Frage 20 — Privileged Deployment Architecture

Sie stellst folgende Struktur fest:

```
Domain Admins
    |
    +-- svc_deploy
    |
    +-- Server-Admins
          |
          +-- Deployment-Team
```

Die Deployment-Plattform verwendet `svc_deploy` und kann auf hunderten Servern administrative Aktionen remote ausführen.

Welche Aussagen sind angemessen?

A. `svc_deploy` sollte als besonders schützenswertes Credential betrachtet werden.

B. Die Deployment-Plattform stellt eine bedeutende Trust Relationship dar.

C. Die Mitglieder des `Deployment-Teams` sollten darauf untersucht werden, welchen Einfluss sie auf das Deployment-System haben.

D. Automatisierung macht privilegierten Zugriff grundsätzlich sicherer.

E. Die tatsächlich benötigten Berechtigungen des Accounts sollten mit seinen aktuellen Domain-Admin-Rechten verglichen werden.

F. Das Audit sollte sowohl die AD-Berechtigungen als auch das Security Model der Deployment-Plattform berücksichtigen.

---

# Teil III — Linux


## Frage 20

Sie führen folgenden Befehl aus:

chmod 644 /etc/example.conf

Welche Aussagen sind akorrekt?

A. Die Datei gehört jetzt root.

B. Die Datei ist jetzt verschlüsselt.

C. Die Datei kann jetzt von jedem lokalen Benutzer geändert werden.

D. Der Befehl ändert die Gruppe der Datei.

E. Der Befehl ändert den Inhalt der Datei.



## Frage 21 — File Permissions

Gegeben ist:

```
-rwxr-x---
```

Welche Aussagen sind korrekt?

A. Der Owner besitzt Read-, Write- und Execute-Rechte.

B. Die Group besitzt Read- und Execute-Rechte.

C. Andere Benutzer besitzen gemäß diesen Mode Bits keine Berechtigungen.

D. Mitglieder der Group können die Datei verändern.

E. Der Owner kann die Datei ausführen.

---

## Frage 22 — Process Enumeration

Welche Commands können nützliche Informationen über laufende Prozesse liefern?

A. `ps aux`

B. `top`

C. `pgrep`

D. `chmod`

E. `systemctl`

---

## Frage 23 — Linux Networking

Während der Analyse eines potenziellen Datenabflusses (Data Exfiltration) auf einem Linux-Applikationsserver müssen Sie aktive Netzwerkverbindungen im Userspace mit den Sockets im Kernel abgleichen sowie Routing-Entscheidungen ohne aktiven Netzwerkverkehr validieren.

Welche Aussagen zu den vorgeschlagenen Diagnosebefehlen sind **korrekt**? 

- **A.** Der Befehl `ip route get <Ziel-IP>` ermittelt die exakte Routing-Entscheidung des Kernels für ein Paket, ohne dass dabei tatsächlicher Netzwerkverkehr generiert wird.

- **B.** Mit `ss -lntup` lassen sich alle lauschenden TCP/UDP-Sockets inklusive der zugehörigen Prozess-IDs (PIDs) und Programmnamen anzeigen. Dies schlägt jedoch fehl, wenn der Befehl ohne `root`-Rechte (oder entsprechende Capabilities) ausgeführt wird.

- **C Der Aufruf von `ip addr` liest die Link-Layer- und Network-Layer-Konfiguration direkt aus dem `/proc`-Dateisystem aus und erzwingt einen hardwareseitigen Link-Status-Check (NIC-MII-Probe).
  
- **D** `chmod` kann über das Setzen des SUID-Bits auf Netzwerk-Binärdateien wie `tcpdump` dazu genutzt werden, um Raw-Socket-Capturing für unprivilegierte Benutzer permanent freizuschalten, ohne Linux Capabilities nutzen zu müssen.
  
- **E** `resolvectl status` liefert zuverlässige Informationen über die aktuell vom systemd-resolved-Dienst genutzten Upstream-DNS-Server pro Interface was statisch in der Datei `/etc/hosts` definiert ist.

---

## Frage 24 — systemd

Welche Aussagen sind korrekt?

A. `systemctl list-unit-files --state=enabled` kann aktivierte systemd Units anzeigen.

B. `systemctl --type=service --state=running` kann aktuell laufende Services anzeigen.

C. `enabled` und `running` sind grundsätzlich dasselbe.

D. Ein Service kann laufen, ohne für den automatischen Start aktiviert zu sein.

E. Diese Commands können nützliche Informationen für ein Securityaudit liefern.

---

## Frage 25 — SSH Configuration

Sie finden folgenden CLI output:

```
/etc/ssh/sshd_config

PermitRootLogin yes
PasswordAuthentication yes
Port 22
```

Welche Aussagen sind angemessen?

A. Root Login ist durch diese Einstellung erlaubt, sofern keine andere anwendbare Konfiguration dies überschreibt.

B. Password Authentication ist durch diese Einstellung erlaubt, sofern keine andere anwendbare Konfiguration dies überschreibt.

C. Port 22 bedeutet, dass SSH-Datenverkehr unverschlüsselt ist.

D. Die Konfiguration sollte mit den Anforderungen der Organisation an administrativen Zugriff verglichen werden.

E. Die Konfiguration allein beweist, dass SSH aus dem Internet erreichbar ist.

---

## Frage 26 — Linux Logging

Welche Quellen können relevante Security-Evidenz auf einem Linux-System liefern?

A. `journalctl`

B. `/var/log/auth.log` auf Systemen, die diese Logging-Konfiguration verwenden

C. `/var/log/secure` auf Systemen, die diese Logging-Konfiguration verwenden

D. `auditd`

E. `/etc/passwd` als primäres Log für Authentication Events

---

## Frage 27 — Package Management

Ein Linux-Server (`Ubuntu`) nutzt ein internes Repository für die Firmen-Software `corp-validator` (v2.1.0) sowie ein externes Drittanbieter-Repository. Es ist kein `Apt Pinning` konfiguriert. Ein Angreifer lädt ein Kompromitiertes Paket mit demselben Namen `corp-validator` und der Version `9.9.9` in das externe Repository hoch.

Welche Aussagen sind **korrekt**? 

**A.** Der Paketmanager ignoriert das externe Paket, da das interne Repo in der `sources.list` weiter oben steht.

**B** Das Kompromitiertes Paket kann bereits während der Installation Schadcode als `root` ausführen (z. B. via `postinst`-Skript).

**C** Um das Risiko zu beheben, muss ein Apt-Pinning mit einer Priorität über 1000 (`Pin-Priority: 1001`) für das interne Repo eingerichtet werden.

**E.** GPG-Schlüssel-Signaturen (`Signed-By`) verhindern diesen Angriff automatisch, wenn beide Repositories gültig signiert sind.



---

## Frage 28 — Linux Capabilities

Ein Scanner meldet:

```
/usr/bin/custom-tool
cap_net_raw+ep
```

Welche Aussagen sind korrekt?


A. `cap_net_raw` steht mit Operationen in Zusammenhang, die Raw-/Packet-Networking betreffen.

B. Linux Capabilities können bestimmte Privilegien gewähren, ohne sämtliche Root-Privilegien zu vergeben.

C. Das Vorhandensein dieser Capability beweist , dass die Binary verwundbar ist.

D. Dem Binary wurde eine Linux Capability zugewiesen.


---

## Frage 29 — Service- und Filesystem-Zusammenhang

Sie finden folgenden CLI Output:

```
/etc/systemd/system/audit.service

[Service]
User=root
ExecStart=/opt/audit/collector
```

und:

```
-rwxrwxr-x root auditors /opt/audit/collector
```

Welche Aussagen sind angemessen?

A. Der Service führt den Collector als Root aus.

B. Mitglieder der Group `auditors` besitzen offenbar Write-Rechte auf den Collector.

C. Eine Änderung des Collectors könnte sich auf Code auswirken, der durch den Root-Service ausgeführt wird.

D. Die Konfiguration beweist, dass das System bereits kompromittiert wurde.

E. Der Zusammenhang zwischen Service-Privilegien und Filesystem-Rechten sollte untersucht werden.

---

## Frage 30 — Integrierte Linux Security Architecture

Sie finden:

```
backup.service

[Service]
User=root
ExecStart=/opt/backup/backup.sh
```

Berechtigungen:

```
-rwxrwxr-x root backupops /opt/backup/backup.sh
```

Group:

```
backupops:
    alice
    bob
    charlie
```

Außerdem:

```
sudo -l -U alice

(root) /bin/systemctl restart backup.service
```

Welche Aussagen sind korrekt?



A. Mitglieder der Gruppe `backupops` können das Script gemäß den angezeigten Berechtigungen verändern.

B. Alice kann den als Root laufenden Service neu starten.

C. Alice besitzt damit eine relevante administrative Beziehung zu einem Root-Execution-Path(`$PATH` des **Root-Benutzers**).

D. Alice besitzt uneingeschränkten Root-Shell-Zugriff.

E. Die gesamte Konfiguration stellt eine Security Boundary dar, die untersucht werden sollte.

F. Das Backup-Script wird vom Service mit Root-Rechten ausgeführt.


