# scwifi

This is a basic component for configuring wifi access.

There is an example project [here](./examples/basic_wifi/README.md).

You can add it to your project by running:

```bash
idf.py add-dependency sethcurry/scwifi
```

You can set your SSID and password with `idf.py menuconfig` under the "WiFi settings" option.

From there, just import the header and call `start_wifi()`. E.g.:

```
#include "scwifi.h"

void app_main(void)
{
	// I believe this is required for wifi to work
	esp_err_t ret = nvs_flash_init();
  	if (ret == ESP_ERR_NVS_NO_FREE_PAGES || ret == ESP_ERR_NVS_NEW_VERSION_FOUND) {
		ESP_ERROR_CHECK(nvs_flash_erase());
		ret = nvs_flash_init();
	}

	start_wifi();
}
```
