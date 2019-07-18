## pelion-rhio-l476-bc95-v01
Fork of pelion-example-rhombio-l476dmw1k project adpated to BC95. Thus, replacing rhomb.io ESP8266 wifi module by rhomb.io NB-IoT (based on Quectel BC95) one.

### Setup your environment

1. Make sure that you have Mbed CLI over 1.9.1
   ```
   C:\>mbed --version
   1.9.1
   ```
   For instruction on how to upgrade Mbed CLI, please refer to this [link](https://github.com/ARMmbed/mbed-cli).

2. Get the whole test code via `mbed import git@github.com:guialonsoalb/pelion-rhio-l476-bc95-v01`

   It will automatically expand dependent libraries in the test SW.

3. Get mbed_cloud_dev_credential.c file from the Pelion portal.

   Then overwrite the existing mbed_cloud_dev_credential.c file.

4. Install the `CLOUD_SDK_API_KEY`

   `mbed config -G CLOUD_SDK_API_KEY ak_1MDE1...<snip>`

   For convenience, this repository uses pre-generated certificates for API key `ak_1MDE1ZjZlMzg4ZTVkMDI0MjBhMDExYjA4MDAwMDAwMDA016617c30d482200d95670ee000000006iCt30Oe5HufoIQbyhTo1ybH00EZviYo`. It's recommended that you generate your own API key as some of the tests (e.g. LWM2M Post) are limited to 1 open active connection to the Pelion DM API server at a time. You should use this key only if you don't have access to Pelion Device Management (which is free to register for any Mbed developer - therefore go register now!).

   For instructions on how to generate your API key, please [see the documentation](https://cloud.mbed.com/docs/current/integrate-web-app/api-keys.html#generating-an-api-key).   

5. Initialize firmware credentials (optional)

   Simple Pelion DM Client provides Greentea tests to test your porting efforts. Before running these tests, it's recommended that you run the `mbed dm init` command, which will install all needed credentials for both Connect and Update Pelion DM features. You can use the following command:
   ```
   $ cd guialonsoalb/pelion-rhio-l476-bc95-v01
   $ mbed dm init -d "<your company name in Pelion DM>" --model-name "<product model identifier>" -q --force
   ```
   If above command do not work for your mbed-cli, please consider upgrading Mbed CLI.

6. Modify any file as needed (main.cpp, mbed_app.json, etc)
7. Compile and program: `mbed compile -t <toolchain> -m RHOMBIO_L476DMW1K -f`