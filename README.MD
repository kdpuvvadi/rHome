# rHome

esphome device for controlling waterpump in our farm.

## Backstory

The motor controller for the farm is located approximately 100 meters from the farmhouse. The farm only gets three-phase power at night. Power failures during the night are also quite common. It can be challenging to check on the motor in the farm during the night due to the presence of snakes and large wild cats that roam freely, making the task tiresome and difficult.

## Present Sollution

A relay has been added to latch on while pressing the 'ON' button of the starter. However, in the event of a power failure or the need to turn off the motor, someone needs to be at the controller to press the 'OFF' button.

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
