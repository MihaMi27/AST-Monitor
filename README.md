# AST-Monitor --- A wearable Raspberry Pi computer for cyclists

This repository is devoted to the AST-monitor, i.e. a low-cost and efficient embedded device for monitoring the realization of sport training sessions that is dedicated to monitor cycling training sessions.
AST-Monitor is a part of Artificial Sport Trainer (AST) system. First bits of AST-monitor were presented in the following [paper](https://arxiv.org/abs/2109.13334).

## Outline of this repository

This repository presents basic code regarded to GUI. It was ported from the initial prototype to poetry.

## Hardware outline

The complete hardware part is shown in Fig from which it can be seen that the AST-computer is split into the following pieces:

* a platform with fixing straps that attach to a bicycle,
* the Raspberry Pi 4 Model B micro-controller with Raspbian OS installed,
* a five-inch LCD touch screen display,
* a USB ANT stick,
* Adafruit's Ultimate GPS HAT module.

<p align="center">
  <img width="200" src=".github/img/complete_small.JPG">
</p>


A Serial Peripheral Interface (SPI) protocol was dedicated for communication between the Raspberry Pi and the GPS peripheral. A specialized USB ANT stick was used to capture the HR signal. The screen display was connected using a modified (physically shortened) HDMI cable, while the touch feedback was implemented using physical wires. The computer was powered during the testing phase using the Trust's (5 VDC) power-bank. The AST-Monitor prototype is still a little bulky, but a more discrete solution is being searched for, including the sweat drainer of the AST.

## Software outline

### Dependencies

List of dependencies:

| Package      | Version    | Platform |
| ------------ |:----------:|:--------:|
| PyQt5        | ^5.15.6    | All      |
| matplotlib   | ^3.5.1     | All      |
| geopy        | ^2.2.0     | All      |
| openant        | v0.4     | All      |
| pyqt-feedback-flow       | ^0.1.0     | All      |
| tcxreader       | ^0.3.8     | All      |
| sport-activities-features       | ^0.2.9     | All      |

Note: openant package should be installed manually. Please follow to the [official instructions](https://github.com/Tigge/openant). If you use Fedora OS, you can install openant package using dnf package manager:

```sh
$ dnf install python-openant
```

## Installation

Install AST-monitor with pip:

```sh
$ pip install ast-monitor
```
In case you want to install directly from the source code, use:

```sh
$ git clone https://github.com/firefly-cpp/AST-Monitor.git
$ cd AST-Monitor
$ poetry build
$ python setup.py install
```

## Deployment

Our project was deployed on Raspberry Pi device using Raspbian OS.

### Run AST-Monitor on startup

Add following lines in /etc/profile which ensures to run scripts on startup:

```sh
sudo python3 /home/user/AST-Cycling.py
sudo nohup python3 /home/user/hr_monitor.py &
sudo nohup python3 /home/user/gps_monitor.py &
```
## Examples

## License

This package is distributed under the MIT License. This license can be found online at <http://www.opensource.org/licenses/MIT>.

## Disclaimer

This framework is provided as-is, and there are no guarantees that it fits your purposes or that it is bug-free. Use it at your own risk!

## Reference

Fister Jr, I., Fister, I., Iglesias, A., Galvez, A., Deb, S., & Fister, D. (2021). On deploying the Artificial Sport Trainer into practice. arXiv preprint [arXiv:2109.13334](https://arxiv.org/abs/2109.13334).
