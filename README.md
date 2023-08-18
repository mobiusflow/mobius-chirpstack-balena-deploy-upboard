# mobius-chirpstack-balena-deploy-upboard

MobiusFlow® and Chirpstack deploy for balena-Hub (Up Board)

## About

MobiusFlow is a scalable, device and protocol agnostic IoT system that can enable an increase
in global efficiencies, reduce environmental impact and waste, whilst connecting millions of devices
via numerous ecosystems, across multiple locations, to be analysed and acted upon remotely based on
actual real-time data.

A huge range of sensors can be connected to MobiusFlow® to transmit the relevant data to multiple
sources for analysis and actions based on agreed parameters for each device, environment or combined
with third party data such as local weather stations to adjust systems accordingly.

Visit https://www.mobiusflow.com for more information, training, and documentation.

## Licensing

In order to use MobiusFlow you must obtain a license code. You can contact us at https://www.mobiusflow.com/contact-us
to request a code.

## Setting up Your Device

### MobiusFlow®

After deploying MobiusFlow to your device, override the following device variables:

- MOBIUS_HUB_ID: 000001 (the MobiusFlow® hub ID for this device)

- MOBIUS_LICENCE = {replace with your licence code}

### Chirpstack

Create an MQTT broker service in MobiusFlow with the following settings

- TCP Port: 1883

- Security: Require Username and Password

- Add a user with name 'chirpstack' and your own secret password

Override the following device variables:

- CHIRPSTACK_MQTT_PWD: The MQTT chirpstack user password you chose in the step above

- INTEGRATION**MQTT**AUTH**GENERIC**PASSWORD: The MQTT chirpstack user password you chose in the step above

## Switching between the MobiusFlow UI and the Chirpstack UI

The MobiusFlow UI is served locally on port 80 and the Chirpstack UI is served locally on port 8080.

When using the Balena public device URL you can only view one UI at a time. This is a Balena limitation. It is however possible to switch between the MobiusFlow and Chirpstack UIs by overriding the NGINX_UI_CONTAINER device variable. The settings are:

- mobius:80 for the MobiusFlow UI

- chirpstack:8080 for the Chirpstack UI

It is recommended that you delete this variable from the fleet device variables and add it to each device but only to the nginx service. This will stop all services from restarting when you change it

## Chirpstack configuration files

The chirpstack configuration files (chirpstack service and chirpstack-gateway-bridge service) for can be modified by hand if required. They are located as shown below:

- chirpstack service: /etc/chirpstack

- chirpstack-gateway-service: /etc/chirpstack-gateway-bridge
