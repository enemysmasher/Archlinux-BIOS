<div align="center">
  
<img src="https://user-images.githubusercontent.com/43359077/120787762-f9cc9080-c52f-11eb-9762-6bfe73111e38.png" alt="drawing" width="500"/>

<div align="left"> 

##### Jak zainstalować Arch Linux krok po kroku ze zrzutami ekranu. Krótko: Ten samouczek pokazuje, jak zainstalować Arch Linux w łatwych do wykonania krokach. Obrazy instalacyjne Archa dostępne są do pobrania tutaj : https://www.archlinux.org/download/ Po pobraniu ISO utwórz rozruchowe urządzenie USB za pomocą polecenia dd Linux.
  
```markdown
# sudo dd if=path-to-image.iso  of=/dev/sdX bs=4M 
  (Zastąp image.iso, np archlinux-2021.06.01-x86_64.iso)
  (Zastąp sdX nazwą urządzenia, np.)
```
##### Natomiast do wykonania bootowalnego pendrive-a pod Windowsem najlepiej jest użyć programu Etcher -> https://www.balena.io/etcher/ lub Ventoy -> https://www.ventoy.net/en/index.html. Wypalamy obraz przy pomocy programu UltraISO-> https://www.ultraiso.com np płycie a następnie uruchamiamy system z wybranego nośnika. Po uruchomieniu ujrzymy ekran do wyboru wersji systemu 32 lub 64 bitowy.
#### Przed instalacją:  
##### **Ethernet** - podłącz kabel sieciowy. Na czas instalacji podepnij się do internetu najlepiej przez kabel. 
##### **Wi-Fi** - połącz się z siecią bezprzewodową za pomocą **iwctl**. Połącz się z **Wi-Fi** za pomocą terminala w Arch Linux i innych dystrybucjach.
#### 1. Konfiguracja Wi-Fi – sieci bezprzewodowe
##### Mój komputer obsługuje **Wi-Fi**, używam go bezpośrednio. Połączenie **Wi-Fi** **(iwctl)**
```yaml
root@archiso ~ # iwctl
```
```yaml
[iwd]# Device List
```
```yaml
[iwd]# station wlan0 get-networks 
```
```yaml
[iwd]# static wlan0 connect "ssid" 
```
#### 2. Połącz się z Internetem
```markdown
# ping -c 5 google.pl
```
##### **Wynik podobny do tego poniżej oznacza, że połączenie działa**
<img src="https://user-images.githubusercontent.com/43359077/120820318-b7697a80-c554-11eb-8004-0cdd49df8a41.png" alt="drawing" width="800"/>
#### 3. Układ klawiatury
##### **By wybrać polski układ klawiatur**
```markdown
# loadkeys pl
```
```markdown
# setfont Lat2-Terminus16
```
##### **przed:**
  
<img src="https://user-images.githubusercontent.com/43359077/120823058-4d9ea000-c557-11eb-9375-418e847a4cf4.png" alt="drawing" width="800"/>

##### **po:**
  
<img src="https://user-images.githubusercontent.com/43359077/120829346-96f1ee00-c55d-11eb-826a-3fe5b2bf2d40.png" alt="drawing" width="800"/>

#### 4. Zaktualizuj systemowy zegar
```markdown
# timedatectl set-ntp true
```
##### **By sprawdzić stan usługi, użyj** 
```markdown
# timedatectl status
```
<img src="https://user-images.githubusercontent.com/43359077/120824727-01ecf600-c559-11eb-8dc6-e117247fafd2.png" alt="drawing" width="800"/>
  
#### 5. Partycjonuj dyski
##### W przypadku, gdy dysk twardy jest nowy, tak jak w przypadku maszyny wirtualnej lub chcesz ponownie podzielić dysk na partycje, uruchom to polecenie, aby utworzyć nową tablicę partycji.
##### **Wipefs** to polecenie czyści tablice partycji, kasuje wszystko z dysku. Potem **cfdisk** i wybierasz **dos**. Potem lecisz już z instalacją Archa.

**Przygotowanie dysku:**
##### DOS (BIOS z MBR)

| Potrzebny | Partycja  | Typ partycji   | Punkt montażu | Flagi      |
|-----------|-----------|----------------|---------------|------------|
| ❌        | /dev/sdXY | Linux swap     | -             | -          |
| ✔️        | /dev/sdXY | Linux          | /mnt          | Bootowalny |
| ❌        | /dev/sdXY | Linux          | /mnt/home     | -          |
 
##### Przy tym kroku należy postępować ostrożnie ponieważ można przypadkiem usunąć partycje.
  
##### Na początek musimy odnaleźć dysk, na którym nasz system ma być zainstalowany.
```markdown
# fdisk -l
```
<img src="https://user-images.githubusercontent.com/43359077/120830795-29df5800-c55f-11eb-8719-29a27ce35004.png)
```markdown
# wipefs -a /dev/sda 
```
<img src="https://user-images.githubusercontent.com/43359077/120843200-1d163080-c56e-11eb-82af-1ee05d1dd587.png" alt="drawing" width="800"/>

**Graficzny (zalecany dla początkujących)**
```markdown
# cfdisk /dev/sda
```
**Wybierz typ tabeli dos** 
 
<img src="https://user-images.githubusercontent.com/43359077/120828770-3367c080-c55d-11eb-8dcd-606b561db8d2.png" alt="drawing" width="800"/>

Osobiście zalecam **minimalne** granice rozmiaru na **/** ustalić w przedziale **10 - 50GB**, oraz całą resztę dostępnej przestrzeni na **/home**.
  


 Rozmiary według uznania :smirk:

