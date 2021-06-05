Update 06 June 2021...

Terima kasih kepada Niezarm yg telah berkongsi config beliau utk reset kwh apabila mendapat bill
dari tnb di mana ianya berlainan utk tiap rumah. Rumah saya 24hb dan rumah Niezarm 13hb. Sebelum
ini saya gunakan helper utk reset kwh counter bila 24hb. Cara Niezarm lagi mudah...

https://github.com/Niezarm/TNB_billing_Calculation

....................................................................

platform: template

sensors:

finaltnb_bill24hb:

friendly_name: "Final Bill TNB 24hb"

unit_of_measurement: 'RM'

icon_template: mdi:currency-usd

value_template: >

{% set O = states('sensor.2monthly_energy_kwh_normal') | float %}

{{ (O * 0.218) |round(2) }}       
    

2monthly_energy_kwh:

source: sensor.energy_spent

cycle: monthly

tariffs:

normal
      
..............................................................................

Kena letak tariff, baru call service keluar utk utility_meter.reset

kemudian kena tambah automation

Config saya akan diperkemaskan semula utk guna cara ini...


# bill_tnb_ha
bill tnb using home assistant
kena tambah dari existing config file

kena tambah helper.. number input utk correct meter reading
![image](https://user-images.githubusercontent.com/63136346/120095742-19437200-c15a-11eb-9686-c66ac7f1b201.png)
kena tambah helper.. number input utk tnb24hb yg kena keyin manually tiap bulan lepas tnb baca meter. refer ke actual tnb bill utk tahu last meter reading value

https://www.youtube.com/watch?v=3o9a9HwUETk
![image](https://user-images.githubusercontent.com/63136346/120095937-3e84b000-c15b-11eb-90c6-6d310ba9f5d7.png)

![image](https://user-images.githubusercontent.com/63136346/120095974-7e4b9780-c15b-11eb-9f41-935c17bff35d.png)





referrence

https://www.home-assistant.io/integrations/utility_meter/

https://www.home-assistant.io/integrations/statistics/

https://www.home-assistant.io/integrations/template/

https://learn.openenergymonitor.org/electricity-monitoring/ct-sensors/interface-with-arduino

https://esphome.io/components/sensor/ct_clamp.html

https://esphome.io/devices/esp32.html
