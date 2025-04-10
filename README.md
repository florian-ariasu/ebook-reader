## OpenBook eBook Reader

Proiect hardware open-source dedicat realizarii unui e-book reader portabil, accesibil si usor de reprodus. Dispozitivul se bazeaza pe un microcontroller ESP32-C6, include un afisaj E-Paper cu consum redus de energie, stocare pe card microSD, conectivitate USB-C pentru alimentare si transfer de date, precum si o baterie Li-Po reincarcabila pentru portabilitate completa.

### Status proiect
- schematic: complet
- pcb: complet
- model 3d: complet
- Gerber: realizat
- CPL: realizat
- BOM: realizat

### Detalii Implementare

#### Diagrama Bloc

[Diagrama Bloc](Images/diagram.png)

`Diagrama bloc reprezinta legatura dintre principalele componente:`
- ESP32-C6 (unitate centrala)
- Afisaj E-Paper
- Cititor SD card
- RTC DS3231
- Senzor ambiental BME688
- Control incarcare baterie Li-Po
- Modul flash extern 64MB
- Interfata USB-C
- Circuit de reglare tensiune (LDO)

---

### BOM - Bill Of Materials

[Fisier BOM](Manufacturing/BOM.csv)

---

### Descrierea hardware-ului

#### Microcontroller
- **ESP32-C6** este unitatea principala care controleaza toate perifericele.
- Ruleaza firmware-ul ce gestioneaza interfata cu utilizatorul, afisajul EPD, comunicatia cu SD card-ul, senzorul ambiental si RTC-ul.

#### Alimentare
- Alimentare principala prin **USB-C**.
- Reglator de tensiune **LDO** (IC4 - XC6204A33) converteste 5V in 3.3V.

#### Stocare
- Slot **microSD** pentru carti si fisiere.
- Memorie flash externa **W25Q512JVSIQ** conectata prin SPI pentru firmware suplimentar sau caching.

---

### Alocarea pinilor ESP32-C6

| Functie               | Pin ESP32-C6 | Observatii |
|------------------------|--------------|-------------|
| SD Card                | IO2, IO3, IO4, IO5 | SPI |
| E-Paper Display        | IO8, IO9, IO10 | SPI |
| Senzor BME688          | IO6 (SCL), IO7 (SDA) | I2C |
| RTC DS3231             | IO6 (SCL), IO7 (SDA) | I2C shared |
| Flash extern SPI       | IO0, IO1, IO2 | SPI |
| Boot Button            | IO9          | Reset GPIO |
| Buton IO               | IO10         | Control interfata |
| UART Debug             | IO20 (TX), IO21 (RX) | Conexiune seriala |
| Ecran Type Select      | IO18, IO19   | Selectare tip e-paper |

---

### Randari & Poze

- In directorul `Images/` am adaugat imagini cu [schematic ul](Images/schematic.png), [pcb ul pe layer ul top](Images/pcb-top.png), [pcb ul pe layer ul botom](Images/pcb-bottom.png), cat si [modelul 3d](Images/3d-model.png), produsul final.

### Bug uri intampinate
- Am fost nevoit sa dau approve pentru 2 erori de tip `Smd-hole` la partea de rutare a pcb ului.

### Link uri piese:
- [Mouser](https://eu.mouser.com/)
- [Comet](https://www.comet.srl.ro/)
