<div align="center">
  
<img src="https://user-images.githubusercontent.com/43359077/120787762-f9cc9080-c52f-11eb-9762-6bfe73111e38.png" alt="logo" width="500"/>

<div align="left"> 

##### Jak zainstalować Arch Linux krok po kroku ze zrzutami ekranu. Krótko: Ten samouczek pokazuje, jak zainstalować Arch Linux w łatwych do wykonania krokach. Obrazy instalacyjne Archa dostępne są do pobrania tutaj : https://www.archlinux.org/download/ Po pobraniu ISO utwórz rozruchowe urządzenie USB za pomocą polecenia **dd** Linux.
  
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
<img src="https://user-images.githubusercontent.com/43359077/120820318-b7697a80-c554-11eb-8004-0cdd49df8a41.png" alt="ping" width="800"/>

#### 3. Układ klawiatury
##### **By wybrać polski układ klawiatur**
```markdown
# loadkeys pl
```
```markdown
# setfont Lat2-Terminus16
```
###### **przed:**
  <img src="https://user-images.githubusercontent.com/43359077/120823058-4d9ea000-c557-11eb-9375-418e847a4cf4.png" alt="setfont" width="800"/>

###### **po:**
  <img src="https://user-images.githubusercontent.com/43359077/120829346-96f1ee00-c55d-11eb-826a-3fe5b2bf2d40.png" alt="setfont" width="800"/>

#### 4. Zaktualizuj systemowy zegar
```markdown
# timedatectl set-ntp true
```
##### **By sprawdzić stan usługi, użyj** 
```markdown
# timedatectl status
```
<img src="https://user-images.githubusercontent.com/43359077/120824727-01ecf600-c559-11eb-8dc6-e117247fafd2.png" alt="timedatectl" width="800"/>
  
#### 5. Partycjonuj dyski
##### W przypadku, gdy dysk twardy jest nowy, tak jak w przypadku maszyny wirtualnej lub chcesz ponownie podzielić dysk na partycje, uruchom to polecenie, aby utworzyć nową tablicę partycji.
##### **Wipefs** to polecenie czyści tablice partycji, kasuje wszystko z dysku. Potem **cfdisk** i wybierasz **dos**. Potem lecisz już z instalacją Archa.

##### **Przygotowanie dysku:**
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
<img src="https://user-images.githubusercontent.com/43359077/120830795-29df5800-c55f-11eb-8719-29a27ce35004.png" alt="fdisk" width="800"/>

```markdown
# wipefs -a /dev/sda 
```
<img src="https://user-images.githubusercontent.com/43359077/120843200-1d163080-c56e-11eb-82af-1ee05d1dd587.png" alt="wipefs" width="800"/>

##### **Graficzny (zalecany dla początkujących)**
##### cfdisk – szybciej, wygodniej, lepiej?
###### Ja preferuje cfdisk - prosta i przejrzysta :hearts:

```markdown
# cfdisk /dev/sda
```
##### Po uruchomieniu otrzymasz monit w ten sposób:
##### **Wybierz typ tabeli dos** 
  
<img src="https://user-images.githubusercontent.com/43359077/120856378-0e387980-c580-11eb-814e-49e0a23268dc.png" alt="dos" width="800"/>

##### Następnie musimy utworzyć odpowiednio partycje **/** i **/home**.
##### Osobiście zalecam **minimalne** granice rozmiaru na **/** ustalić w przedziale **10 - 50GB**, oraz całą resztę dostępnej przestrzeni na **/home**.
##### Teraz zobaczysz tabelę partycji w ten sposób:
##### Zobacz dostępne wolne miejsce. Tutaj mamy 1000GB. Wybierz NOWY i utwórz nową partycję.
<img src="https://user-images.githubusercontent.com/43359077/120857870-3aed9080-c582-11eb-8b7f-b93bd4cbb286.png" alt="nowy" width="800"/>
 

##### Przykład: Wybierz rozmiar **40GB**. Chcemy główną, zatem wciskamy enter.
<img src="https://user-images.githubusercontent.com/43359077/120857878-3d4fea80-c582-11eb-81c8-b5fa3f9e128b.png" alt="partycja_40GB" width="800"/>
  
##### wybierz podstawowy
<img src="https://user-images.githubusercontent.com/43359077/120857891-42149e80-c582-11eb-8f9a-3bfd213a9908.png" alt="podstawowy" width="800"/> 
  
##### wybierz **Bootable** (flaga rozruchowa)
<img src="https://user-images.githubusercontent.com/43359077/120857905-4640bc00-c582-11eb-886a-9493169eeba4.png" alt="boot" width="800"/> 
  
##### Flaga boot jest potrzebna dla linux
<img src="https://user-images.githubusercontent.com/43359077/120867570-7c863780-c592-11eb-80d0-98f55e59d413.png" alt="flaga_bootowalna" width="800"/>

##### Pozwoli ci to na utworzenie kolejnych, dodatkowych partycji.
##### Jeśli chcesz utworzyć więcej partycji to skonfiguruj partycję **sda2** jako **podstawowy** **(Primary)**, podziel ją w/g uznania a następnie zapisz nowy partycji dysku wybierając **(Write)**.
<img src="https://user-images.githubusercontent.com/43359077/120871900-587c2380-c59d-11eb-8c47-f3c76ab3d379.png" alt="dodatkowy_nowy" width="800"/>
  
##### Naciśnij klawisz Enter, aby zaakceptować domyślny.
<img src="https://user-images.githubusercontent.com/43359077/120871905-5ade7d80-c59d-11eb-8375-4f3cbeed3af5.png" alt="partycja_960GB" width="800"/>
  
##### wybierz podstawowy
<img src="https://user-images.githubusercontent.com/43359077/120871910-5d40d780-c59d-11eb-9564-b977d68f0ad7.png" alt="podstawowy" width="800"/>
  
##### Skończone. Partycja utworzona w miły i przyjemny sposób. Możemy zapisać teraz zmiany używając opcji **Write**.
<img src="https://user-images.githubusercontent.com/43359077/120871915-5fa33180-c59d-11eb-8c5e-728e60fb7d61.png" alt="write" width="800"/>
  
##### Wpisz **yes**, aby zatwierdzić zmiany w strukturze dysku, a następnie naciśnij klawisz Enter.
  <img src="https://user-images.githubusercontent.com/43359077/120871918-616cf500-c59d-11eb-8a20-763592c48951.png" alt="yes" width="800"/>
  
##### Przed ostatecznym zapisem system poprosi was o potwierdzenie. Aby wyjść bez zapisywania zmian należy wybrać Zakończ.
##### cfdisk zapisze zmiany na wirtualnym napędzie dysków. cfdisk wyświetli następujący komunikat diagnostyczny:
##### Po zakończeniu działań programu wyjdź wybierając Quit.
  
<img src="https://user-images.githubusercontent.com/43359077/120871922-6336b880-c59d-11eb-9713-c4356958c52f.png" alt="quit" width="800"/>

##### Jak widać na dysku są 2 partycje.
```markdown
# fdisk -l
```
<img src="https://user-images.githubusercontent.com/43359077/120871970-882b2b80-c59d-11eb-8d3c-0ac5a6420ef1.png" alt="fdisk-l"/>

##### Jesteśmy gotowi, by przejść powoli do instalacji bazowego systemu. Nowe partycje należy sformatować za pomocą systemu plików, zanim będzie można ich używać. Możesz to zrobić za pomocą odpowiedniego polecenia mkfs.
  
#### 5. Formatowanie partycji BIOS with MBR
##### Pozostałe dwie partycje można sformatować w dowolnym systemie plików Linux. Polecam użycie ext4
```markdown
# mkfs.ext4 -L root /dev/sda1
# mkfs.ext4 -L home /dev/sda2
```
<img src="https://user-images.githubusercontent.com/43359077/120876910-e531dc00-c5b3-11eb-990a-6479a4cf3a4f.png" alt="mkfs" />

#### 6. Zamontuj system plików
##### Teraz nadszedł czas na zamontowanie tych partycji:
```markdown
# mount /dev/sda1 /mnt
# mkdir /mnt/home
# mount /dev/sda2 /mnt/home
```
##### Sprawdź punkty montażowe, czy zostały pomyślnie utworzone
```markdown
lsblk -f
```
  

  

  
 
