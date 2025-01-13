# Dokumentácia k navrhnutej sieti a konfigurácii
## Konfigurácia servera
### Radius Server (Server-PT)
- **IP adresa:** 192.168.0.10
- **Služby:**
  - Zapnutá AAA (Authentication, Authorization, Accounting)
  - Konfigurácia hesiel a užívateľských mien pre IoT zariadenia.
  - **Prístupové údaje:**
    - Meno: Home 
    - Secret: pass123

### Pridanie IoT zariadení
- Zoznam IoT zariadení pridaných na server:
  - AC (Air Conditioner)
  - Dvere
  - Light
  - Light
  - Door
  - Garage Door
  - Humidity Monitor
  - Humidifier
  - Fan
  - Lawn Sprinkler
  - Appliance
  - Furnace
  - Thermostat
- Každému zariadeniu boli priradené unikátne užívateľské meno a heslo.
- ip adresy boli zariadeniam automaticky priradené

---

## Konfigurácia sieťových zariadení

### Switch
- Použitý model: **2960-24TT**
- Prepojenie:
  - FastEthernet0/2 zo switchu do Ethernet1 v bezdrôtovom smerovači.

### Bezdrôtový smerovač (WRT300N)
- **SSID:** Home
- **Bezpečnosť:** WPA2 Enterprise
  - Centrálna autentifikácia pomocou Radius Servera.
  - **Radius server IP:** 192.168.0.10
  - **Shared secret:** pass123
- Ostatné nastavenia ponechané na predvolenej hodnote.

### IoT zariadenia
- Každé zariadenie:
  - **Network Adapter:** PT-IOT-NM-1W-AC
  - **SSID:** Home
  - **Autentifikácia:** WPA2 s priradeným užívateľským menom a heslom.

### IoT Server Remote Access
- Zapnutá služba IoT Server Remote Access.
- Konfigurácia:
  - **IP adresa servera:** 192.168.0.10
  - **Používateľské meno:** Home
  - **Heslo:** Home

### Dodatočný smerovač (HomeRouter-PT-AC)
- Zapnuté heslo pre 2,4 GHz sieť.
- **Heslo:** CISCOCISCO (jednoduché heslo pre domácu sieť).

---

## Konfigurácia koncových zariadení

### Notebooky
- Zmenený modul na **PT-LAPTOP-NM-1W-AC** (podpora 5 GHz siete).
- Priradené IP adresy:
  - Notebook 1: 192.168.0.99
  - Notebook 2: 192.168.0.98

### Tablet
- Nakonfigurovaný rovnakým spôsobom ako notebooky s ip adresou 192.168.0.97

### Počítač
- **Pripojenie:** Káblovo k bezdrôtovému smerovaču (GigabitEthernet).
- **IP adresa:** 192.168.0.96
- **Modul:** PT-HOST-NM-1CGE (Gigabit Ethernet pripojenie).

---

## Prístup k správe IoT zariadení
- Na ktoromkoľvek z pripojených zariadení otvorte webový prehliadač.
- Zadajte **IP adresu servera:** 192.168.0.10.
- Prihláste sa pomocou užívateľského mena a hesla alebo si vytvorte účet ak nemáte.
- Správa IoT zariadení:
  - Pridávanie podmienok pre spustenie zariadení.
  - Monitorovanie a ovládanie pripojených IoT zariadení.

---

# Bezpečnostné riziká

- Užívateľská sieť nemá žiadne overovanie ako pri IoT zariadeniach.
- Ak by sa niekto pripojil a vedel by heslo na IoT server, mohol by ovládať zariadenia. Predpokladá sa, že na domácej sieti netreba overovať užívateľov, no tým, že je sieť bezdrôtová, môžu sa pripojiť ľudia mimo domácnosti, ak poznajú heslo.
- Je možné fyzicky sa pripojiť k switchu a ak niekto pozná heslo na IoT server, mohol by ovládať zariadenia.
- Aktuálne sú heslá slabé.
- Ak by sa použilo niečo ako VLAN na oddelenie IoT zariadení od užívateľov, bolo by to bezpečnejšie.

---

# Chyby v Cisco Packet Tracer

- Keď som dorobil projekt, všetky IoT zariadenia boli pripojené na sieť, no po uložení a následnom otvorení sa iba niektoré zo zariadení pripojili. Skúšal som projekt viacnásobne vypnúť a zapnúť, ale vždy sa iba niektoré (vždy iné zariadenia) pripoja.
- Kontroloval som všetky nastavenia zariadení, ale problém zrejme nie je v konfigurácii, pretože každé zariadenie sa už aspoň raz pripojilo, no nie všetky naraz.

