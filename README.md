# OpenBook eBook Reader

Proiect hardware open-source dedicat realizării unui e-book reader portabil, accesibil și ușor de reprodus. Dispozitivul se bazează pe un microcontroller ESP32-C6, include un afișaj E-Paper cu consum redus de energie, stocare pe card microSD, conectivitate USB-C pentru alimentare și transfer de date, precum și o baterie Li-Po reîncărcabilă pentru portabilitate completă.

## Diagramă Bloc

[Diagramă Bloc](Images/diagram.png)

> Diagrama bloc prezintă legătura între principalele componente:
- ESP32-C6 (unitate centrală)
- Afișaj E-Paper
- Cititor SD card
- RTC DS3231
- Senzor ambiental BME688
- Control încărcare baterie Li-Po
- Modul flash extern 64MB
- Interfață USB-C
- Circuit de reglare tensiune (LDO)

---

## BOM - Bill Of Materials

[Fisier BOM](Images/BOM.csv)

---

## Descrierea hardware-ului

### Microcontroller
- **ESP32-C6** este unitatea principală care controlează toate perifericele.
- Rulează firmware-ul ce gestionează interfața cu utilizatorul, afișajul EPD, comunicația cu SD card-ul, senzorul ambiental și RTC-ul.

### Alimentare
- Alimentare principală prin **USB-C**.
- Reglator de tensiune **LDO** (IC4 - XC6204A33) convertește 5V în 3.3V.

### Stocare
- Slot **microSD** pentru cărți și fișiere.
- Memorie flash externă **W25Q512JVSIQ** conectată prin SPI pentru firmware suplimentar sau caching.

---

## Alocarea pinilor ESP32-C6

| Funcție               | Pin ESP32-C6 | Observații |
|------------------------|--------------|-------------|
| SD Card                | IO2, IO3, IO4, IO5 | SPI |
| E-Paper Display        | IO8, IO9, IO10 | SPI |
| Senzor BME688          | IO6 (SCL), IO7 (SDA) | I2C |
| RTC DS3231             | IO6 (SCL), IO7 (SDA) | I2C shared |
| Flash extern SPI       | IO0, IO1, IO2 | SPI |
| Boot Button            | IO9          | Reset GPIO |
| Buton IO               | IO10         | Control interfață |
| UART Debug             | IO20 (TX), IO21 (RX) | Conexiune serială |
| Ecran Type Select      | IO18, IO19   | Selectare tip e-paper |

---

## Randări & Poze

- In directorul `Images/` am adaugat imagini cu schematicul, pcb ul, cat si modelul 3d, realizat partial.
- Nu am reusit sa termin modelul 3d din cauza acestei erori: [Err](Images/err.png)

