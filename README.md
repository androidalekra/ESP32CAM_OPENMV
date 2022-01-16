# micropython for ESP32CAM with OPENMV(OPENCV)

modul ESP32CAM u TME
+ https://www.tme.eu/cz/details/wt-esp32-cam/vyvojove-kity-ostatni/wireless-tag/

tenpa1105 poskládal firmware micropythonu pro ESP32 (M5camera) s knihovnou IMAGE podobnou OPENCV pro počítačové vidění
+ https://github.com/tenpa1105/M5Camera_OpenMV

OPENMV je projekt původně pro micropython STM32
+ https://openmv.io/

dokumentace pro ESP32
+ https://wiki.sipeed.com/soft/maixpy/en/api_reference/machine_vision/image/image.html

při použití firmwaru
+ https://github.com/tenpa1105/M5Camera_OpenMV/tree/main/firmware

na ESP32CAM je třeba nastavit io piny takto

```python
camera.init(0, d0=5, d1=18, d2=19, d3=21, d4=36, d5=39, d6=34, d7=35,
            format=camera.RGB565, framesize=camera.FRAME_QVGA, xclk_freq=camera.XCLK_10MHz,
            href=23, vsync=25, reset=-1, pwdn=32, sioc=27, siod=26, xclk=0, pclk=22)
 ```
 
 záměnou modcamera.h z originílního uložiště
 
 + https://github.com/lemariva/micropython-camera-driver/blob/master/src/modcamera.h
 
 pak stačí
 
 ```python
camera.init(0, framesize=camera.FRAME_QCIF, format=camera.RGB565)
```

upravený firmware uložen

+ https://github.com/androidalekra/ESP32CAM_OPENMV/tree/main/firmware_esp32cam


**postřehy:**

**ESP32CAM má SPIRAM o velikosti 8MB. ESP32 umí bez speciálního ovladače, který není součástí micropythonu, přímo adresovat jen 4MB.
Ovladač kamery používá 2MB jako obrazovou cache a miropythonu zbude 2MB na práci :-(**
