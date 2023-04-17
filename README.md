# pkt_fwd_raspbian

Todo o processo de instalação do Ppacket Forwarder teve ajuda do [AdailSilva](https://github.com/AdailSilva) sem ele a curva de aprendizado e desenvolvimento seria muito mais lenta.

```
sudo apt update
sudo apt -y upgrade
sudo apt-get update 

git clone https://github.com/elcereza/pkt_fwd_raspbian
git clone https://github.com/kersing/lora_gateway.git
git clone https://github.com/kersing/paho.mqtt.embedded-c.git
git clone https://github.com/kersing/ttn-gateway-connector.git
git clone https://github.com/kersing/protobuf-c.git
git clone https://github.com/kersing/packet_forwarder.git
git clone https://github.com/google/protobuf.git

sudo apt -y install protobuf-compiler &&
sudo apt -y install libprotobuf-dev &&
sudo apt -y install libprotoc-dev &&

sudo apt-get -y install automake &&
sudo apt -y install libtool &&
sudo apt -y install autoconf &&

sudo apt -y install libftdi1 &&
sudo apt -y install libftdi-dev &&
sudo apt -y install swig &&
sudo apt -y install python-dev &&
sudo apt -y search libusb &&
sudo apt -y install libusb-1.0-0 &&
sudo apt -y install libusb-1.0-0-dev &&

cd packet_forwarder
cd mp_pkt_fwd/
sudo rm -rf build-pi.sh
sudo cp /home/pi/pkt_fwd_raspbian/build-pi.sh ./
sudo chmod +x ./build-pi.sh
sudo ./build-pi.sh

cd /opt/elcereza
sudo cp /home/pi/pkt_fwd_raspbian/global_conf.json ./
sudo cp /home/pi/pkt_fwd_raspbian/start.sh ./
sudo chmod +x start.sh
sudo chown pi:pi start.h
sudo chown pi:pi mp_pkt_fwd
sudo chown pi:pi global_conf.json

cd /lib/systemd/system
sudo cp /home/pi/pkt_fwd_raspbian/elcereza.service ./
sudo chmod +x elcereza.service
sudo chown pi:pi elcereza.service

sudo systemctl daemon-reload
sudo systemctl enable elcereza.service
sudo systemctl start elcereza.service
sudo systemctl status elcereza.service

cd /home/pi
sudo rm -rf lora_gateway
sudo rm -rf packet_forwarder
sudo rm -rf paho.mqtt.embedded-c
sudo rm -rf protobuf
sudo rm -rf protobuf-c
sudo rm -rf ttn-gateway-connector
sudo rm -rf pkt_fwd_raspbian
```
