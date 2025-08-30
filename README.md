# temperature_monitoring
Temperature monitoring is the process of measuring and tracking temperature levels in various environments, systems, or applications. This can be done using temperature sensors, which convert temperature readings into electrical signals that can be processed and analyzed.
#include <OneWire.h>
#include <DallasTemperature.h>

const int oneWireBus = 2; // Pin for DS18B20 sensor
OneWire oneWire(oneWireBus);
DallasTemperature sensors(&oneWire);

void setup() {
  Serial.begin(9600);
  sensors.begin();
}

void loop() {
  sensors.requestTemperatures();
  float temperature = sensors.getTempCByIndex(0);
  Serial.print("Temperature: ");
  Serial.print(temperature);
  Serial.println("°C");
  delay(1000);
}
