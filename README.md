# Arduino Instrumentasi – ESP-NOW Communication

Repository ini berisi kumpulan program implementasi komunikasi nirkabel antarperangkat mikrokontroler ESP8266 menggunakan protokol ESP-NOW. Proyek ini berfokus pada penerapan komunikasi data dalam sistem instrumentasi, khususnya pengiriman data hasil pembacaan sensor.

## Metode Komunikasi

### 1. Many-to-One (MTO)
Metode komunikasi dari beberapa perangkat transmitter menuju satu perangkat receiver.

```text
ESP8266 (Sensor 1) ──┐
ESP8266 (Sensor 2) ──┼──> ESP8266 (Receiver)
ESP8266 (Sensor 3) ──┘
```

### 2. One-to-Many (OTM)
Metode komunikasi dari satu perangkat transmitter menuju beberapa perangkat receiver.

```text
                  ┌──> ESP8266 (Receiver 1)
ESP8266           ├──> ESP8266 (Receiver 2)
(Transmitter) ────┤
                  └──> ESP8266 (Receiver 3)
```

### 3. Point-to-Point (PTP)
Metode komunikasi langsung antara satu transmitter dan satu receiver.

```text
ESP8266 (Transmitter) ────> ESP8266 (Receiver)
```

## Hardware
- ESP8266 NodeMCU
- Sensor DHT11
- Breadboard
- Kabel jumper
- Komputer atau laptop

## Software dan Library
- Arduino IDE
- ESP8266 Board Package
- ESP8266WiFi
- ESP-NOW
- DHT Sensor Library

## Struktur Repository

```text
Arduino-Instrumentasi/
│
├── MTO/
│   ├── Transmitter/
│   └── Receiver/
│
├── OTM/
│   ├── Transmitter/
│   └── Receiver/
│
├── PTP/
│   ├── Transmitter/
│   └── Receiver/
│
└── README.md
```

## Format Data

Data sensor dikirim menggunakan struktur data (struct).

```cpp
typedef struct struct_message {
    uint8_t DEV_ID = 1;
    float hum;
    float temp;
} struct_message;
```

| Variabel | Keterangan |
|---|---|
| DEV_ID | Identitas perangkat |
| hum | Kelembapan udara (%) |
| temp | Temperatur (°C) |

## Prinsip Kerja Program
1. Inisialisasi komunikasi Wi-Fi ESP8266.
2. Inisialisasi protokol ESP-NOW.
3. Konfigurasi alamat MAC perangkat tujuan.
4. Pembacaan data sensor DHT11.
5. Pengiriman data melalui ESP-NOW.
6. Penerimaan data pada perangkat receiver.
7. Monitoring data melalui Serial Monitor.

## Cara Penggunaan
1. Install Arduino IDE.
2. Install ESP8266 Board Package.
3. Install library DHT Sensor.
4. Hubungkan ESP8266 ke komputer.
5. Pilih folder metode komunikasi MTO, OTM, atau PTP.
6. Sesuaikan alamat MAC setiap perangkat.
7. Upload program transmitter dan receiver.
8. Buka Serial Monitor untuk melihat hasil komunikasi.

**Catatan:** Pastikan konfigurasi channel Wi-Fi, alamat MAC, dan peer ESP-NOW sudah sesuai pada setiap perangkat.

## Perbandingan Metode Komunikasi

| Parameter | MTO | OTM | PTP |
|---|---|---|---|
| Transmitter | Banyak | Satu | Satu |
| Receiver | Satu | Banyak | Satu |
| Komunikasi | Banyak ke satu | Satu ke banyak | Satu ke satu |

## Tujuan Proyek
- Memahami komunikasi ESP-NOW pada ESP8266.
- Mengimplementasikan topologi MTO, OTM, dan PTP.
- Mengirimkan data sensor secara wireless.
- Memahami penggunaan alamat MAC.
- Mempelajari proses pengiriman dan penerimaan data.
- Mengembangkan sistem instrumentasi berbasis komunikasi nirkabel.

## Penutup

Repository ini diharapkan menjadi referensi pembelajaran implementasi komunikasi wireless pada sistem instrumentasi berbasis ESP8266 menggunakan protokol ESP-NOW.

**Platform:** ESP8266  
**Protocol:** ESP-NOW  
**Sensor:** DHT11  
**Language:** C/C++ (Arduino)
