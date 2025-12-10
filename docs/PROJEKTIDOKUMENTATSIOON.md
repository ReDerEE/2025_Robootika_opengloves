# Projekti dokumentatsioon

## 1. Projekti eesmärk ja seadme lühikirjeldus
**Mis asi see on, mida ja miks me teeme? Millist praktilist probleemi see lahendab?**

- Meie projekti eesmärk on luua haptilised kindad, mida saab kasutada virtuaal reaalsues (VR), virutaalsete objektide tunnetamiseks.
- Seade annab võimaluse oma enda kätega tunnetada virtuaalseid objekte, aitab kaasa virtuaal reaalsuse immersiooniga.
- Peamised komponendid: ESP32 mikrokontroller, akupangad, servomootorid, joystick, potentsiomeetrid, nupp, vedrud, nöörid, 3d prinditud osad kinnitamiseks ja kandmiseks. 

---

## 2. Sisendite loetelu
**Millised on süsteemi poolt loetavad / mõõdetavad sisendid? Millega neid mõõdetakse / tuvastatakse?**

- Potentsiomeetrid:
  - Väikesõrme painutus -> analoogpinge loetakse ESP32 pinilt **PIN_PINKY (36)**
  - Nimetissõrme painutus -> analoogpinge ESP32 pinilt **PIN_RING (39)**
  - Keskmise sõrme painutus -> analoogpinge ESP32 pinilt **PIN_MIDDLE (34)**
  - Nimetissõrme painutus -> analoogpinge ESP32 pinilt **PIN_INDEX (35)**
  - Pöidla painutus -> analoogpinge ESP32 pinilt **PIN_THUMB (32)**

- Joystick
  - Joystick X-telg -> analoogpinge ESP32 pinilt **PIN_JOY_X (12)**
  - Joystick Y-telg -> analoogpinge ESP32 pinilt **PIN_JOY_Y (14)**
  - Joystick vajutusnupp -> digitaalne sisend ESP32 pinilt **PIN_JOY_BTN (26)**

- Bluetooth sisend -> Saab kätte mootorite kontrollimiseks vajaliku informatsiooni.
---

## 3. Väljundite loetelu
**Mida süsteem teeb / muudab? Millega väljund realiseeritakse?**

- Sõrmede jõutagasiside (force feedback):
  Osutavad vastupanu, kui kasutaja puudutab midagi virtuaal reaalsuses.
  - Väikesõrme servo/mootor -> **PIN_PINKY_MOTOR (5)**
  - Nimetissõrme servo/mootor -> **PIN_RING_MOTOR (18)**
  - Keskmise servo/mootor -> **PIN_MIDDLE_MOTOR (19)**
  - Nimetissõrme servo/mootor -> **PIN_INDEX_MOTOR (16)**
  - Pöidla servo/mootor -> **PIN_THUMB_MOTOR (17)**

- Debug LED -> **LED (PIN 2)**

- Bluetooth väljund -> Saadab sõrmede asendid, Žestide olekud, Joysticki asendi.

---

## 4. Nõuded loodavale seadmele
**Mis peab toimuma, kui kasutaja teeb mingi toimingu? Kirjelda käitumisloogika.**

- Kui näpp liigutatakse, siis see saadab näppude painduvuse edasi, siis driver tõlgendab seda Valve Knuckles grip väärtuseks.
- Kui kasutaja liigutab käe interactible objekti lähedusse, siis see paneb servod käima, et kasutaja ei saaks objekti mõistes näppe sellest läbi pista(force feedback osa)
- Kui kasutaja liigutab joystick'i, siis see saadetakse driver'ile ja see tõlgib seda reaalsel kasutatavaks vr joystick'i liigutuseks 

---

## 5. Süsteemi füüsiliste komponentide loetelu
**Millest seade koosneb? Lisa lingid või täpsed nimed, et keegi teine saaks sama asja uuesti osta / teha.**

Tabelina või punktidena. Nt:

- _(1x) ESP32-WROOM-32U WROVER_ [Aliexpress](https://www.aliexpress.com/item/1005008209898668.html?spm=a2g0o.order_list.order_list_main.35.30fa1802Zp5XaK&gatewayAdapt=4itemAdapt)
- _(2x) Xiaomi Redmi Power Bank (20000mAh)_ [Arvutitark](https://arvutitark.ee/en/smart-devices/smart-device-accessories/akupangad/xiaomi-redmi-fast-charge-power-bank-20000-mah-black-18-w-1017875)
- _(5x) MG90S Micro Servo Motor (180)_ [Aliexpress](https://www.aliexpress.com/item/1005005672961991.html?spm=a2g0o.order_list.order_list_main.20.30fa1802Zp5XaK)
- _(1x) Joystick, Joystick for Arduino Dual-axis_ [Aliexpress](https://www.aliexpress.com/item/1005007915984781.html?spm=a2g0o.order_list.order_list_main.30.30fa1802Zp5XaK)
- _(5x) Rotary Potentiometer (6mm, 3 pin, 10K ohm) [Aliexpress](https://www.aliexpress.com/item/33011428749.html?spm=a2g0o.order_list.order_list_main.25.30fa1802Zp5XaK)
- _(1x) Momentary Push Button Switch_  [Aliexpress_ET](https://www.aliexpress.com/item/4001081730289.html?spm=a2g0o.order_list.order_list_main.40.30fa1802Zp5XaK) [Aliexpress_EN](https://www.aliexpress.us/item/2255800895415537.html?spm=a2g0o.order_list.order_list_main.40.30fa1802Zp5XaK&gatewayAdapt=glo2usa4itemAdapt)
- _(5x) Vedru ja (5x) Nööri (Saadud lingitud toote lahti lammutamisel.)_ [Aliexpress](https://www.aliexpress.us/item/3256803821144861.html?spm=a2g0o.order_list.order_list_main.45.30fa1802Zp5XaK&gatewayAdapt=glo2usa4itemAdapt)
- _Kaablid_ [Aliexpress](https://www.aliexpress.com/item/1005007156114505.html?spm=a2g0o.order_list.order_list_main.50.30fa1802Zp5XaK)
- _Kaablite otsad_ [Aliexpress](https://www.aliexpress.com/item/1005007425641197.html?spm=a2g0o.order_list.order_list_main.15.30fa1802Zp5XaK)
- _3D prinditud osad_ (hardware/3D kaustas)

---

## 6. Ühendusskeem
**Kuidas kõik osad on omavahel ühendatud?**
[hardware/wiring-diagram.png]

- Väikesõrme Potentsiomeeteri asend -> **PIN_PINKY (36)**
- Nimetissõrme Potentsiomeeteri asend -> **PIN_RING (39)**
- Keskmise sõrme Potentsiomeeteri asend -> **PIN_MIDDLE (34)**
- Nimetissõrme Potentsiomeeteri asend -> **PIN_INDEX (35)**
- Pöidla Potentsiomeeteri asend -> **PIN_THUMB (32)**

- Joystick X-telg asend -> **PIN_JOY_X (12)**
- Joystick Y-telg asend -> **PIN_JOY_Y (14)**
- Joystick nupu vajutus -> **PIN_JOY_BTN (26)**

- Väikesõrme servo/mootor -> **PIN_PINKY_MOTOR (5)**
- Nimetissõrme servo/mootor -> **PIN_RING_MOTOR (18)**
- Keskmise servo/mootor -> **PIN_MIDDLE_MOTOR (19)**
- Nimetissõrme servo/mootor -> **PIN_INDEX_MOTOR (16)**
- Pöidla servo/mootor -> **PIN_THUMB_MOTOR (17)**

- Väikesõrme Potentsiomeeter ground -> **PIN(GROUND)**
- Nimetissõrme Potentsiomeeter ground -> **PIN(GROUND)**
- Keskmise sõrme Potentsiomeeter ground -> **PIN(GROUND)**
- Nimetissõrme Potentsiomeeter ground -> **PIN(GROUND)**
- Pöidla Potentsiomeeter ground -> **PIN(GROUND)**
- Väikesõrme servo/mootor ground -> **PIN(GROUND)**
- Nimetissõrme servo/mootor ground -> **PIN(GROUND)**
- Keskmise servo/mootor ground -> **PIN(GROUND)**
- Nimetissõrme servo/mootor ground -> **PIN(GROUND)**
- Pöidla servo/mootor ground -> **PIN(GROUND)**
- Joystick ground -> **PIN(GROUND)**
- Nupp ground -> **PIN(GROUND)**
- Vooluallika ground -> **PIN(GROUND)**

- Vooluallikas 1 -> **PIN(5V/Voltage In)** või **USB-C Input**
- Vooluallikas 2 -> Kõik servomootorid

- **PIN(3.3V)** -> Väikesõrme Potentsiomeeteri vool
- **PIN(3.3V)** -> Nimetissõrme Potentsiomeeteri vool
- **PIN(3.3V)** -> Keskmise sõrme Potentsiomeeteri vool
- **PIN(3.3V)** -> Nimetissõrme Potentsiomeeteri vool
- **PIN(3.3V)** -> Pöidla Potentsiomeeteri vool
- **PIN(3.3V)** -> Joystick vool

---

## 7. Süsteemi juhtiv kood (või pseudokood)
**Kirjelda programmi loogikat nii, et seda on võimalik aru saada ka hiljem.**  
Kui kood töötab, pane siia lühike selgitus + viide failile `src/projektinimi.ino`.  
Kui kood pole veel valmis, lisa siia pseudokood.
