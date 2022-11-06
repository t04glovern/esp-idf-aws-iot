# ESP-IDF AWS IoT

## Steps

* Install [PlatformIO Core](http://docs.platformio.org/page/core.html)
* Create a device and export the three certificates to:
  * `src/aws-root-ca.pem`: Retrieve from [HERE](https://www.amazontrust.com/repository/AmazonRootCA1.pem)
  * `src/private.pem.key`: Private Key Certificate
  * `src/certificate.pem.crt`: Device Certificate
* Update `#define CONFIG_AWS_IOT_MQTT_HOST "xxxxxxxxxxxxx-ats.iot.us-east-1.amazonaws.com"` in `sdkconfig.h`
  * Run `aws iot describe-endpoint --endpoint-type iot:Data-ATS` to get address
* Update `build_flags` in `platformio.ini`
  * `-DCONFIG_WIFI_SSID=\"wifissid\"`
  * `-DCONFIG_WIFI_PASSWORD=\"wifipass\"`
  * `-DCONFIG_AWS_IOT_TOPIC=\"test_topic/esp32\"`
* Run these commands:

  ```bash
  # Build project
  platformio run

  # If you get an error `Kconfig.projbuild' not found (in 'source "$COMPONENT_KCONFIGS_PROJBUILD"').`, run this command
  pip3 uninstall kconfiglib

  # Upload firmware
  platformio run --target upload
  ```

## Attribution

* [Espressif 32: development platform for PlatformIO](https://github.com/platformio/platform-espressif32/tree/master/examples/espidf-aws-iot)
