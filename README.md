<div align="center">
  
<img src="https://user-images.githubusercontent.com/43359077/120787762-f9cc9080-c52f-11eb-9762-6bfe73111e38.png" alt="drawing" width="200"/>

<div align="left"> 

## Jak zainstalować Arch Linux krok po kroku ze zrzutami ekranu. Krótko: Ten samouczek pokazuje, jak zainstalować Arch Linux w łatwych do wykonania krokach. Obrazy instalacyjne Archa dostępne są do pobrania tutaj : https://www.archlinux.org/download/ Po pobraniu ISO utwórz rozruchowe urządzenie USB za pomocą polecenia dd Linux.
  
```markdown
# sudo dd if=path-to-image.iso  of=/dev/sdX bs=4M  
  (Zastąp sdX nazwą urządzenia, np.)
```
### Natomiast do wykonania bootowalnego pendrive-a pod Windowsem najlepiej jest użyć programu Etcher -> https://www.balena.io/etcher/ lub Ventoy -> https://www.ventoy.net/en/index.html. Wypalamy obraz przy pomocy programu UltraISO-> https://www.ultraiso.com np płycie a następnie uruchamiamy system z wybranego nośnika. Po uruchomieniu ujrzymy ekran do wyboru wersji systemu 32 lub 64 bitowy.
  
### Przed instalacją:  
**Ethernet** - podłącz kabel sieciowy. Na czas instalacji podepnij się do internetu najlepiej przez kabel. 
**Wi-Fi** - połącz się z siecią bezprzewodową za pomocą **iwctl**. Połącz się z **Wi-Fi** za pomocą terminala w Arch Linux i innych dystrybucjach.
### 1. Konfiguracja Wi-Fi – sieci bezprzewodowe
Mój komputer obsługuje **Wi-Fi**, używam go bezpośrednio. Połączenie **Wi-Fi** **(iwctl)**

**root@archiso ~ # iwctl**


$iwctl
 [IWD] # Device List // list all network devices
  
 [IWD] # station wlan0 get-networks // WiFi wlan0 can be used in the past is my wireless network card, and different device names may be different.
  
 [IWD] # static wlan0 connct ssid // ssid is WiFi name
  
 / / After entering the password, the link is successful



  
