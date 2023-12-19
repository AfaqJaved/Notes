
```c++

#include <WiFi.h>

const char *ssid = "esp32";

const char *password = "12345678";

IPAddress staticIP(192, 168, 1, 1);

IPAddress gateway(192, 168, 1, 1);

IPAddress subnet(255, 255, 255, 0);

WiFiServer wifiServer(80);

void setup() {

  Serial.begin(115200);

  delay(1000);

  // Set up Access Point
  WiFi.softAP(ssid, password);
  delay(100);

  // Configure static IP address for the Access Point
  WiFi.softAPConfig(staticIP, gateway, subnet);
  Serial.println("Access Point IP address: " + WiFi.softAPIP().toString());
  wifiServer.begin();

}

void loop() {

  WiFiClient client = wifiServer.available();

  if (client) {

    while (client.connected()) {

      while (client.available()>0) {

        char c = client.read();

        client.write(c);

      }

      delay(10);

    }

    client.stop();

    Serial.println("Client disconnected");

  }
}
```
