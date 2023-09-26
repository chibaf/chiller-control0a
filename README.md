# chiller-control0a

# chiller-control0

# UART経由のchiller制御

chiller-control program via UART

<img width="740" alt="selecting2-chiller" src="https://github.com/chibaf/chiller_communcations/assets/1296728/8e1d3e94-d953-46b3-ae54-6b2bd1dc4fa9">

<img width="778" alt="Screen Shot 2023-09-18 at 20 33 46" src="https://github.com/chibaf/chiller_communcations/assets/1296728/81a852b2-82bb-46ea-8762-c740f424cd2d">

## （1）BCCの計算

pythonの対話モードで

＞＞＞ 0x53^0x31^0x20^0x20^0x20^0x20^0x32^0x30^0x2e^0x30^0x03

125

＞＞＞ hex(125)

0x7d

## (2) chillerの設定温度の取得: temp1.py on Raspberry Pi

＞＞＞ import serial

＞＞＞ ser = serial.Serial('/dev/ttyUSB0',9600,timeout=1)

＞＞＞ get_temp = b'\x04\x30\x30\x53\x31\x05'

＞＞＞ ser.write(get_temp)

6

＞＞＞ line = ser.readline() 

＞＞＞ print(line)

b'\x02S1    20.0\x03}'

＞＞＞ line2 = line.strip().decode("utf-8")

＞＞＞ b=line2.split()

＞＞＞ print("setting temp ",b[1][:-1])

setting temp  20.0

## (3) real time plotting: real_time_plot_temp_from_chiller.py

usage: python3 real_time_plot_temp_from_chiller.py

or

usage: python3 real_time_plot_temp_from_chiller.py filename.csv

<img width="1349" alt="chiller-temp-plot" src="https://github.com/chibaf/chiller-control0/assets/1296728/8739af76-1340-439a-9f3a-435399b9fbb6">
