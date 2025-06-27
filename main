#include <SPI.h>
#include <MFRC522.h>

#define SS_PIN 10
#define RST_PIN 9
MFRC522 rfid(SS_PIN, RST_PIN);

String validUIDs[] = {
  "DE 4B 3A 91",
  "74 B3 2F 11",
  "A2 9C 47 88",
  "3F 7D 1A C0",
  "19 FA 6E 22"
};

int totalUIDs = 5;
unsigned long lastMessageTime = 0;
unsigned long messageInterval = 3000;

void setup() {
  Serial.begin(9600);
  SPI.begin();
  rfid.PCD_Init();
  Serial.println("RFID Attendance System Initialized.");
}

void loop() {
  if (!rfid.PICC_IsNewCardPresent() || !rfid.PICC_ReadCardSerial()) {
    if (millis() - lastMessageTime > messageInterval) {
      Serial.println("Waiting for card...");
      lastMessageTime = millis();
    }
    return;
  }

  String scannedUID = "";
  for (byte i = 0; i < rfid.uid.size; i++) {
    scannedUID += String(rfid.uid.uidByte[i], HEX);
    if (i < rfid.uid.size - 1) scannedUID += " ";
  }
  scannedUID.toUpperCase();

  Serial.print("Scanned UID: ");
  Serial.println(scannedUID);

  bool isValid = false;
  for (int i = 0; i < totalUIDs; i++) {
    if (scannedUID == validUIDs[i]) {
      isValid = true;
      break;
    }
  }

  if (isValid) {
    Serial.println("Attendance marked successfully.");
  } else {
    Serial.println("Unrecognized card. Access denied.");
  }

  rfid.PICC_HaltA();
  rfid.PCD_StopCrypto1();
  delay(1000);
}
