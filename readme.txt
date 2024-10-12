Ros2 ile arduinoya topic yolu ile mesaj publish edilerek led açıp kapatılmıştır.

Windows üzerinde SerialtoIp.exe ile arduinonun bulunduğu comp port tcp server yapılmıştır.

Linux'da açılan tcp servera virtual com port ile aşağıdaik gibi bağlanılmıştır:

1. Terminal

sudo socat  pty,link=/dev/virtualcom0,raw  tcp:192.168.1.104:5000 (Bazen sonunda '&' olabiliyor.)

2. Terminal(Sıra ile)

sudo chmod o+rw /dev/virtualcom0

stty 115200 < /dev/virtualcom0

sudo stty 115200 -F /dev/virtualcom0

Daha sonra publisher başlatılır:

ros2 run arduinobot_python_firmware simple_serial_transmitter.py --ros-args -p port:=/dev/virtualcom0

Daha sonra mesaj gönderilir:

ros2 topic pub --once /serial_transmitter std_msgs/msg/String "data: 'a'"
