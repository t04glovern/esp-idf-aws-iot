# ESP-IDF AWS IoT

## Steps

* Install [PlatformIO Core](http://docs.platformio.org/page/core.html)
* Create a device and export the three certificates to:
  * `src/aws-root-ca.pem`: Retrieve from [HERE](https://www.amazontrust.com/repository/AmazonRootCA1.pem)
  * `src/private.pem.key`: Private Key Certificate
  * `src/certificate.pem.crt`: Device Certificate
* Run these commands:

```bash
# Build project
> platformio run

# Upload firmware
> platformio run --target upload

# Clean build files
> platformio run --target clean
```

## Attribution

* [Espressif 32: development platform for PlatformIO](https://github.com/platformio/platform-espressif32/tree/master/examples/espidf-aws-iot)
