I have a pre-built bin file in the firmware folder. Please write with the following command.

```
pip install esptool
esptool.py --port /dev/ttyUSB0 write_flash 0x8000 partition-table.bin 0x1000 bootloader.bin 0x10000 micropython.bin
```
