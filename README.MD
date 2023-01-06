# rHome

esphome device for controlling waterpump in our farm.

## Backstory

Motor controller is about 100 meters from the farm house. Farm only gets 3 phase power in the night. Power failures in the middle of the night are also pretty common. Checking on motor in the farm middle of the night is tiresum and difficult with snakes and large wild cats are freely roaming.

## Present Sollution

Added a relay to latch on while pressing `ON` button of the starter. But on power failure or in the event of motor needed to be turned off, someone needs to be at the controller and press `OFF` button.

## Sollution

Farm already has [TP-Link EAP225-Outdoor](https://www.tp-link.com/en/business-networking/omada-sdn-access-point/eap225-outdoor/) accesspoint installed and Motor controller location gets 30% signal but we are not pushing any large data.

By enabling the `web_server` component, controls are exposed and anyone in the farm can control the motor by just tap of the button and by setting `local: true`, no need for internet connection to fetch the `ccs/js` assests.

## Logic

- `Motor ON` latches the motor on relay and turns itself of after given period of time.
- `Motor OFF` turns of the motor by removing the latch.
- `Auto ON` is added `restore_mode` with `RESTORE_DEFAULT_OFF`.
  - It'll retain the state and incase power failure or reboot, it'll turn back on and powers on the `Motor On`.
  - By switching off, it'll turn on `Motor OFF`.

## LICENSE

[MIT](/LICENSE)
