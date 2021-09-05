<div align="center">
  
<img src="https://user-images.githubusercontent.com/43359077/124366285-e0ae2100-dc4e-11eb-89dc-affbe96b7945.png" alt="logo" width="1000"/>
 
<div align="left"> 


##### Jak zainstalować Arch Linux krok po kroku ze zrzutami ekranu. Krótko: Ten samouczek pokazuje, jak zainstalować Arch Linux w łatwych do wykonania krokach. Obrazy instalacyjne Archa dostępne są do pobrania tutaj : https://www.archlinux.org/download/ Po pobraniu ISO utwórz rozruchowe urządzenie USB za pomocą polecenia **dd** Linux.
```markdown
# sudo dd if=path-to-image.iso  of=/dev/sdX bs=4M status='progress'
  (Zastąp image.iso, np archlinux-2021.06.01-x86_64.iso)
  (Zastąp sdX nazwą urządzenia, np.)
```
##### Natomiast do wykonania bootowalnego pendrive-a pod Windowsem najlepiej jest użyć programu Etcher -> https://www.balena.io/etcher/ lub Ventoy -> https://www.ventoy.net/en/index.html. Wypalamy obraz przy pomocy programu UltraISO-> https://www.ultraiso.com np płycie a następnie uruchamiamy system z wybranego nośnika. Po uruchomieniu ujrzymy ekran do wyboru wersji systemu 32 lub 64 bitowy.
##### Archlinux jest to świetny system dla naszego desktopa?

#### Spis treści 

* [**Arch Linux - instalacja i konfiguracja**](#arch-linux---instalacja-i-konfiguracja)
* [**Przed instalacją**](#przed-instalacją)
  * [**1. Konfiguracja Wi-Fi – sieci bezprzewodowe**](#1-konfiguracja-wi-fi--sieci-bezprzewodowe)
  * [**2. Połącz się z Internetem**](#2-połącz-się-z-internetem)
  * [**3. Układ klawiatury**](#3-układ-klawiatury)
  * [**4. Zaktualizuj systemowy zegar**](#4-zaktualizuj-systemowy-zegar)
  * [**5. Partycjonuj dyski**](#5-partycjonuj-dyski)
  * [**6. Formatowanie partycji BIOS z MBR**](#6-formatowanie-partycji-bios-z-mbr)
  * [**7. Zamontuj system plików**](#7-zamontuj-system-plików)
  * [**8. Instalacja systemu podstawowego**](#8-instalacja-systemu-podstawowego)
  * [**9. Generowanie fstab**](#9-generowanie-fstab)
  * [**10. Wejdź przez chroot do nowego systemu**](#10-wejdź-przez-chroot-do-nowego-systemu)
  * [**11. Strefa czasowa - Ustaw czas**](#11-strefa-czasowa---ustaw-czas)
  * [**12. Konfiguracja języka**](#12-konfiguracja-języka)
  * [**13. Plik konfiguracyjny dla ustawień regionalnych - Ustaw zmienną**](#13-plik-konfiguracyjny-dla-ustawień-regionalnych---ustaw-zmienną)
  * [**14. Plik konfiguracyjny konsoli wirtualnej - Czcionka konsoli**](#14-plik-konfiguracyjny-konsoli-wirtualnej---czcionka-konsoli)
  * [**15. Ustaw nazwę hosta**](#15-ustaw-nazwę-hosta)
  * [**16. Musisz również dodać tę nazwę do pliku hosts**](#16-musisz-również-dodać-tę-nazwę-do-pliku-hosts)
  * [**17. Konfiguracja sieci**](#17-konfiguracja-sieci)
  * [**18. Włącz sieć**](#18-włącz-sieć)
  * [**19. Tworzenie ramdisc**](#19-tworzenie-ramdisc)
  * [**20. Hasło użytkownika root**](#20-hasło-użytkownika-root)
  * [**21. Mikrokodu**](#21-jeśli-posiadasz-procesor-intela-zainstaluj-pakiet-intel-ucode)
  * [**22. BIOS GRUB**](#22-bios-grub)
  * [**23. TRIM**](#23-teraz-wiele-osób-ma-dyski-ssd-które-obsługują-trim-dla-bezpiecznej-cotygodniowej-usługi-trim-na-dyskach-ssd-i-wszystkich-innych-urządzeniach-które-umożliwiają-obsługę-trim)
  * [**24. Wyjście z chroot**](#24-wyjście-z-chroot)
  * [**25. Logowanie się do systemu**](#25-logowanie-się-do-systemu)
  * [**26. Sprawdź, czy internet wifi**](#26-sprawdź-czy-internet-wifi)
  * [**27. Dodaj użytkownika**](#27-dodaj-użytkownika)
  * [**28. SUDO - nadawanie uprawnień użytkownikom Linux**](#28-nast%C4%99pnie-w%C5%82%C4%85cz-uprawnienia-sudoers-dla-nowo-utworzonego-u%C5%BCytkownika)
  * [**29. Standardowo plik konfiguracyjny Pacmana**](#29-pacmanconf---plik-konfiguracyjny-menedżera-pakietów-pacman)
  * [**30. Xorg**](#30-instalacja-xorg-a)
  * [**31. Sterownik graficzny**](#31-wybieramy-dodatkowo-sterownik-poniżej-dla-swojej-karty-graficznej)
  * [**32. Wybór środowiska pulpitu**](#32-środowisko-pulpitu)
  * [**33. Dźwięk**](#33-dźwięk)
  
  
  * [**the continue ...**](https://i.imgur.com/x08cazS.gif)
  
#### Arch Linux - instalacja i konfiguracja
  
<img src="https://user-images.githubusercontent.com/43359077/121141147-f0e30400-c83a-11eb-9bbc-7da319ae4ef4.png" alt="live_boot" width="800"/>

###### [Do góry](#spis-treści)
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
[iwd]# station wlan0 connect ssid 
```
```yaml
[iwd]# exit
```
###### [Do góry](#spis-treści)
-----  
#### 2. Połącz się z Internetem
```markdown
# ping -c 5 google.pl
```
##### **Wynik podobny do tego poniżej oznacza, że połączenie działa**
<img src="https://user-images.githubusercontent.com/43359077/120820318-b7697a80-c554-11eb-8004-0cdd49df8a41.png" alt="ping" width="800"/>

###### [Do góry](#spis-treści)
-----
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
  
###### [Do góry](#spis-treści)
-----
#### 4. Zaktualizuj systemowy zegar
```markdown
# timedatectl set-ntp true
```
##### **By sprawdzić stan usługi, użyj** 
```markdown
# timedatectl status
```
<img src="https://user-images.githubusercontent.com/43359077/120824727-01ecf600-c559-11eb-8dc6-e117247fafd2.png" alt="timedatectl" width="800"/>
  
###### [Do góry](#spis-treści)
-----
#### 5. Partycjonuj dyski
##### W przypadku, gdy dysk twardy jest nowy, tak jak w przypadku maszyny wirtualnej lub chcesz ponownie podzielić dysk na partycje, uruchom to polecenie, aby utworzyć nową tablicę partycji.
##### **Wipefs** to polecenie czyści tablice partycji, kasuje wszystko z dysku. Potem **cfdisk** i wybierasz **dos**. Potem lecisz już z instalacją Archa.

##### **Przygotowanie dysku:**
##### DOS (BIOS/LEGACY)

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
##### **Wybierz typ tabeli dos**.
  
<img src="https://user-images.githubusercontent.com/43359077/120856378-0e387980-c580-11eb-814e-49e0a23268dc.png" alt="dos" width="800"/>

##### Następnie musimy utworzyć odpowiednio partycje **/** i **/home**.
##### Osobiście zalecam **minimalne** granice rozmiaru na **/** ustalić w przedziale **10 - 50GB**, oraz całą resztę dostępnej przestrzeni na **/home**.
##### Teraz zobaczysz tabelę partycji w ten sposób:
##### Zobacz dostępne wolne miejsce. Tutaj mamy 1000GB. Wybierz **NOWY** i utwórz nową partycję.
<img src="https://user-images.githubusercontent.com/43359077/120857870-3aed9080-c582-11eb-8b7f-b93bd4cbb286.png" alt="nowy" width="800"/>
 
##### Przykład: Wybierz rozmiar **40GB**. Chcemy główną, zatem wciskamy enter.
<img src="https://user-images.githubusercontent.com/43359077/120857878-3d4fea80-c582-11eb-81c8-b5fa3f9e128b.png" alt="partycja_40GB" width="800"/>
  
##### wybierz podstawowy
<img src="https://user-images.githubusercontent.com/43359077/120857891-42149e80-c582-11eb-8f9a-3bfd213a9908.png" alt="podstawowy" width="800"/> 
  
##### wybierz **Bootable** (flaga rozruchowa).
<img src="https://user-images.githubusercontent.com/43359077/120857905-4640bc00-c582-11eb-886a-9493169eeba4.png" alt="boot" width="800"/> 
  
##### Flaga boot jest potrzebna dla linux.
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
  
##### Przed ostatecznym zapisem system poprosi o potwierdzenie. Aby wyjść bez zapisywania zmian należy wybrać Zakończ.
##### cfdisk zapisze zmiany na wirtualnym napędzie dysków. cfdisk wyświetli następujący komunikat diagnostyczny:
##### Po zakończeniu działań programu wyjdź wybierając **Quit**.
##### Tablica partycji zostałą zmodyfikowana.
<img src="https://user-images.githubusercontent.com/43359077/120871922-6336b880-c59d-11eb-9713-c4356958c52f.png" alt="quit" width="800"/>

##### Jak widać na dysku są 2 partycje.
```markdown
# fdisk -l
```
<img src="https://user-images.githubusercontent.com/43359077/120871970-882b2b80-c59d-11eb-8d3c-0ac5a6420ef1.png" alt="fdisk-l" width="800"/>

###### [Do góry](#spis-treści)
-----
##### Jesteśmy gotowi, by przejść powoli do instalacji bazowego systemu. Nowe partycje należy sformatować za pomocą systemu plików, zanim będzie można ich używać. Możesz to zrobić za pomocą odpowiedniego polecenia mkfs.
#### 6. Formatowanie partycji BIOS z MBR
##### Pozostałe dwie partycje można sformatować w dowolnym systemie plików Linux. Polecam użycie ext4.
```markdown
# mkfs.ext4 -L root /dev/sda1
# mkfs.ext4 -L home /dev/sda2
```
<img src="https://user-images.githubusercontent.com/43359077/120876910-e531dc00-c5b3-11eb-990a-6479a4cf3a4f.png" alt="mkfs" width="800"/>
  
###### [Do góry](#spis-treści)
-----
#### 7. Zamontuj system plików
##### Teraz nadszedł czas na zamontowanie tych partycji:
```markdown
# mount /dev/sda1 /mnt
# mkdir /mnt/home
# mount /dev/sda2 /mnt/home
```
<img src="https://user-images.githubusercontent.com/43359077/120877202-7e152700-c5b5-11eb-958c-4cf2f534b8fd.png" alt="mount" width="800"/>

##### Sprawdź punkty montażowe, czy zostały pomyślnie utworzone.
```markdown
# lsblk -f
```
<img src="https://user-images.githubusercontent.com/43359077/120877278-fd0a5f80-c5b5-11eb-835b-1df822c4a560.png" alt="lsblk-f" width="800"/>
  
###### [Do góry](#spis-treści)
----- 
#### 8. Instalacja systemu podstawowego
##### Teraz rozpoczynamy proces instalacji.
##### Pobranie pakietów i instalacja systemu mieści się w jednej komendzie:
```markdown
# pacstrap -i /mnt base base-devel bash-completion linux linux-firmware linux-headers nano dhcpcd
```
##### Dodałem Nano edytor, ponieważ trzeba edytować niektóre pliki po instalacji.
##### Przy pytaniu, jakie pakiety zainstalować wcisnąć ENTER. Poczekaj chwilę, aż się zakończy.
<img src="https://user-images.githubusercontent.com/43359077/122657333-eee64280-d162-11eb-87c6-640034a5877f.png" alt="pacstrap" width="800"/>

##### To zajmie trochę czasu, aby pobrać i zainstalować te pakiety. Jeśli pliki do pobrania zostanie przerwane, nie trzeba panikować. Możesz uruchomić powyższe polecenie jeszcze raz i wznowić pobieranie.
###### [Do góry](#spis-treści)
-----  
#### 9. Generowanie fstab
```markdown
# genfstab -U -p /mnt >> /mnt/etc/fstab
```
##### oraz sprawdzenie czy jest poprawny.
```markdown
# genfstab -U -p /mnt /mnt/etc/fstab
```
<img src="https://user-images.githubusercontent.com/43359077/120879502-13b7b300-c5c4-11eb-9d42-d3f8b5de4a62.png" alt="fstab" width="800"/>
 
###### [Do góry](#spis-treści)
-----
#### 10. Wejdź przez chroot do nowego systemu
```markdown
# arch-chroot /mnt /bin/bash
``` 
<img src="https://user-images.githubusercontent.com/43359077/120879922-24b5f380-c5c7-11eb-9f8b-b1336162493c.png" alt="arch-chroot" width="800"/>

###### [Do góry](#spis-treści)
-----
#### 11. Strefa czasowa - Ustaw czas
```markdown
# ln -sf /usr/share/zoneinfo/Europe/Warsaw /etc/localtime
# hwclock --systohc --utc
```
<img src="https://user-images.githubusercontent.com/43359077/120880081-5f6c5b80-c5c8-11eb-94de-f65bff0a30c7.png" alt="czasowa" width="800"/>

###### [Do góry](#spis-treści)
-----
#### 12. Konfiguracja języka
```markdown
# nano /etc/locale.gen
```
<img src="https://user-images.githubusercontent.com/43359077/120886743-c8b39500-c5ef-11eb-95cb-d7af41100399.png" alt="locale-gen" width="800"/>

##### Za pomocą klawiszy strzałek przewiń ekran w dół i znajdź linię.
```js
#en_US.UTF-8 

#pl_PL.UTF-8
```
##### Odkomentuj go, usuwając znak **#**
```js
en_US.UTF-8

pl_PL.UTF-8
```
zapisać **ctrl+O** (zapisuje), **ENTER** później **ctrl+X** (zamyka nano)
  
<img src="https://user-images.githubusercontent.com/43359077/120886633-3dd29a80-c5ef-11eb-987d-0f59fb69bc8d.png" alt="locale_gen" width="800"/>

##### Następnie musisz wygenerować ustawienia regionalne
```markdown
# locale-gen
```
  
<img src="https://user-images.githubusercontent.com/43359077/120886947-b423cc80-c5f0-11eb-9dff-9df183597f9c.png" alt="generowanie" width="800"/>
  
###### [Do góry](#spis-treści)
-----
#### 13. Plik konfiguracyjny dla ustawień regionalnych - Ustaw zmienną
  
```markdown
# nano /etc/locale.conf
```
<img src="https://user-images.githubusercontent.com/43359077/120887670-86d91d80-c5f4-11eb-9e90-89a4b4499e28.png" alt="locale.conf" width="800"/>

##### wpisać poniższy tekst:
```yaml
LANG=pl_PL.UTF-8
LANGUAGE=pl_PL.UTF-8
LC_ADDRESS=pl_PL.UTF-8
LC_COLLATE=pl_PL.UTF-8
LC_CTYPE=pl_PL.UTF-8
LC_IDENTIFICATION=pl_PL.UTF-8
LC_MONETARY=pl_PL.UTF-8
LC_MESSAGES=pl_PL.UTF-8
LC_MEASUREMENT=pl_PL.UTF-8
LC_NAME=pl_PL.UTF-8
LC_NUMERIC=pl_PL.UTF-8
LC_PAPER=pl_PL.UTF-8
LC_TELEPHONE=pl_PL.UTF-8
LC_TIME=pl_PL.UTF-8
```
zapisać **ctrl+O** (zapisuje), **ENTER** później **ctrl+X** (zamyka nano) 

###### [Do góry](#spis-treści)
-----
#### 14. Plik konfiguracyjny konsoli wirtualnej - Czcionka konsoli.
```markdown
# nano /etc/vconsole.conf
```
<img src="https://user-images.githubusercontent.com/43359077/120888305-dec55380-c5f7-11eb-8f19-d9479ee7fd83.png" alt="vconsole" width="800"/>

##### wpisać poniższy tekst:
```yaml
KEYMAP=pl
FONT=Lat2-Terminus16.psfu.gz
FONT_MAP=8859-2
```
zapisać **ctrl+O** (zapisuje), **ENTER** później **ctrl+X** (zamyka nano) 
###### [Do góry](#spis-treści)
-----  
#### 15. Ustaw nazwę hosta
##### Nazwa hosta to nazwa komputera. Nazwijmy go - archtest
```markdown
# nano /etc/hostname
```
<img src="https://user-images.githubusercontent.com/43359077/120888400-71fe8900-c5f8-11eb-81eb-411357044aa0.png" alt="hostname" width="800"/>

##### wpisać poniższy tekst:
```yaml
archtest
```
zapisać **ctrl+O** (zapisuje), **ENTER** później **ctrl+X** (zamyka nano)
  
###### [Do góry](#spis-treści)
----- 
#### 16. Musisz również dodać tę nazwę do pliku hosts
```markdown
# nano /etc/hosts
```
<img src="https://user-images.githubusercontent.com/43359077/120892829-5a32ff00-c610-11eb-896b-fa3100be471f.png" alt="hosts" width="800"/>

##### wpisać poniższy tekst:
```js
127.0.0.1       localhost
::1             localhost
127.0.1.1       archtest.localdomain        archtest
```
 <img src="https://user-images.githubusercontent.com/43359077/120892943-e1807280-c610-11eb-8eca-13fa8144d5c1.png" alt="localhost" width="800"/>
 
zapisać **ctrl+O** (zapisuje), **ENTER** później **ctrl+X** (zamyka nano) 
###### [Do góry](#spis-treści)
-----
#### 17. Konfiguracja sieci
##### Twój interfejs sieciowy jest wymieniony i włączony. Kabel jest podłączony lub podłączony do bezprzewodowej sieci LAN
##### Aktywuj dhcpcd
```markdown
# systemctl enable dhcpcd
```
<img src="https://user-images.githubusercontent.com/43359077/120892992-31f7d000-c611-11eb-85f6-c67202d97fb9.png" alt="dhcpcd" width="800"/>

###### [Do góry](#spis-treści)
----- 
#### 18. Włącz sieć
##### Najpierw zainstaluj menedżera sieci:
##### Pobranie pakietów i instalacja systemu mieści się w jednej komendzie:
```markdown
# pacman -S networkmanager 
```
##### Konfiguracja sieci
```markdown
# pacman -S iw iwd dialog net-tools wireless_tools wpa_supplicant
```
<img src="https://user-images.githubusercontent.com/43359077/120896952-1944e580-c624-11eb-8ee7-784f76a5c771.png" alt="network" width="800"/>

##### Aktywuj usługi do następnego ponownego uruchomienia
 ```markdown 
# systemctl enable NetworkManager
```
<img src="https://user-images.githubusercontent.com/43359077/120894858-d3375400-c61a-11eb-8fd7-3f03db7c1516.png" alt="enable_networkmanager" width="800"/>

###### [Do góry](#spis-treści)
----- 
#### 19. Tworzenie ramdisc
```markdown
# mkinitcpio -P linux
```
<img src="https://user-images.githubusercontent.com/43359077/120895213-442b3b80-c61c-11eb-808d-300e6d853eb6.png" alt="mkinitcpio" width="800"/>

###### [Do góry](#spis-treści)
-----
#### 20. Hasło użytkownika root
```markdown
# passwd
```
##### Po wciśnięciu ENTER należy dwa razy podać hasło użytkownika root
  
<img src="https://user-images.githubusercontent.com/43359077/120895893-522e8b80-c61f-11eb-9b1b-c9e529b607ec.png" alt="passwd" width="800"/>

###### [Do góry](#spis-treści)
-----
#### 21. Jeśli posiadasz procesor Intela, zainstaluj pakiet intel-ucode.
##### Procesory Intela i Amd potrzebują dodatkowo mikrokodów które będą wczytywane przy bootowaniu systemu.
##### Mikrokod Intela to mikrokod działający w procesorach:
```markdown
# pacman -S intel-ucode
```
<img src="https://user-images.githubusercontent.com/43359077/120896057-1516c900-c620-11eb-94bb-22a6afd58b0b.png" alt="intel" width="800"/>

##### Mikrokod Amd to mikrokod działający w procesorach:
```markdown
# pacman -S amd-ucode
```     
<img src="https://user-images.githubusercontent.com/43359077/120896095-42fc0d80-c620-11eb-949b-dda7a81e6353.png" alt="amd" width="800"/> 

###### [Do góry](#spis-treści)  
-----
#### 22. BIOS GRUB
##### Zainstaluj GRUB
```markdown
# pacman -S grub
# grub-install --target=i386-pc --recheck /dev/sda 
# grub-mkconfig -o /boot/grub/grub.cfg
```
<img src="https://user-images.githubusercontent.com/43359077/120898730-6af16e00-c62c-11eb-8ca1-fe472c493d72.png" alt="grub" width="800"/> 

###### [Do góry](#spis-treści)  
-----
#### 23. Teraz wiele osób ma dyski SSD, które obsługują TRIM. Dla bezpiecznej, cotygodniowej usługi TRIM na dyskach SSD i wszystkich innych urządzeniach, które umożliwiają obsługę TRIM:
```markdown
# systemctl enable fstrim.timer
```
<img src="https://user-images.githubusercontent.com/43359077/120900751-d5a7a700-c636-11eb-828b-12d854702c1b.png" alt="fstrim" width="800"/> 
 
###### [Do góry](#spis-treści)
-----  
#### 24. Wyjście z chroot
```markdown
# exit
```
##### Odmontowanie partycji i restart systemu
```markdown
# umount -Rv /mnt
# reboot
```
##### Jeśli wszystko zrobiłeś poprawnie, po ponownym uruchomieniu zobaczysz ekran powitalny GRUB z zainstalowanym Arch Linux.
<img src="https://user-images.githubusercontent.com/43359077/120901140-58316600-c639-11eb-9d9f-ea33b0c63cc6.png" alt="grub" width="800"/> 

###### [Do góry](#spis-treści)  
-----  
#### 25. Logowanie się do systemu
##### Po ponownym uruchomieniu systemu należy się zalogować wpisując login
```markdown
archtest login: root
```
<img src="https://user-images.githubusercontent.com/43359077/120901471-654f5480-c63b-11eb-806d-743359679deb.png" alt="grub" width="800"/> 

##### Aby kontynuować, zaloguj się jako użytkownik root z wcześniej ustawionym hasłem.

###### [Do góry](#spis-treści)  
-----
#### 26. Sprawdź, czy internet wifi
```markdown
# ip a
```
Jeśli w sieci Wi-Fi należy połączyć się z:
```markdown
# nmtui
```

<img src="https://user-images.githubusercontent.com/43359077/122683344-d88dc480-d1fe-11eb-985f-7af41ad8d1de.png" alt="nmtui" width="800"/> 

###### [Do góry](#spis-treści)  
----- 
#### 27. Dodaj użytkownika
##### Zamiast tego wpisz swoje własne **tester**
```markdown
# useradd -m tester
```
##### Utwórz również hasło dla nowego użytkownika
```markdown
# passwd tester
```
##### Po wciśnięciu ENTER należy dwa razy podać hasło nazwa_użytkownika 
<img src="https://user-images.githubusercontent.com/43359077/120901968-00e1c480-c63e-11eb-9910-20065fb4b193.png" alt="uzytkownik" width="800"/>
 
###### [Do góry](#spis-treści)  
-----
#### 28. Następnie włącz uprawnienia sudoers dla nowo utworzonego użytkownika
##### Najprostsze podstawowe ustawienie można przeprowadzić wydając z konta "root" polecenie:
```markdown
# nano /etc/sudoers
```
##### Za pomocą klawiszy strzałek przewiń ekran w dół i znajdź linię.
```yaml
root ALL=(ALL) ALL
```
##### gdzie "tester ALL=(ALL) ALL" to nazwa zwykłego użytkownika. 
##### wpisać poniższy tekst:
```yaml
tester ALL=(ALL) ALL
```  
**przed**
  
<img src="https://user-images.githubusercontent.com/43359077/120902340-266fcd80-c640-11eb-8777-9d5ddae36df2.png" alt="root1" width="800"/>
 
**po**
  
<img src="https://user-images.githubusercontent.com/43359077/120902346-32f42600-c640-11eb-80bc-6b7862fff742.png" alt="root2" width="800"/>

###### [Do góry](#spis-treści)  
-----
#### 29. Pacman.conf - plik konfiguracyjny menedżera pakietów pacman
##### Włączenie repozytorium z pakietami 32 bit i 64 bit w 64 bitowym systemie Arch Linux (np. wine , steam itp.)
```markdown
# # nano /etc/pacman.conf
```
##### Aby włączyć repozytorium multilib, odkomentuj, usuwając znak **#**
##### Za pomocą klawiszy strzałek przewiń ekran w dół i znajdź linię
###### przed
```yaml
#[multilib]
#Include = /etc/pacman.d/mirrorlist
```
<img src="https://user-images.githubusercontent.com/43359077/122675591-66a38400-d1da-11eb-9309-95cf78d7778f.png" alt="multilib1" width="1000"/>
 
###### po  
```yaml
[multilib]
Include = /etc/pacman.d/mirrorlist
```  
<img src="https://user-images.githubusercontent.com/43359077/122675596-6c996500-d1da-11eb-849c-c9c2a5b88d1a.png" alt="multilib2" width="1000"/>

zapisać ctrl+O -(zapisuje), ENTER później ctrl+X (zamyka nano)

##### Następnie zaktualizuj system i zainstaluj żądane pakiety multilib
```markdown
# pacman -Syu
```
<img src="https://user-images.githubusercontent.com/43359077/122676398-3827a800-d1de-11eb-8ed0-851edb4a9562.png" alt="pacmansyu" width="1000"/>

###### [Do góry](#spis-treści)
-----  
#### 30. Instalacja Xorg-a
##### Są to niektóre pakiety potrzebne do prawidłowego działania niektórych urządzeń wejściowych. Instalacja ich nie szkodzi, nawet jeśli ich nie potrzebujesz
##### Xorg to serwer wyświetlania, którego użyjemy
```markdown
# pacman -S xorg xorg-xinit xterm
```
###### [Do góry](#spis-treści)
-----
#### 31. Wybieramy dodatkowo sterownik poniżej dla swojej karty graficznej
##### Zainstaluj to tylko wtedy, gdy używasz graficznego AMD lub Intel lub chcesz użyć sterownika NVIDIA typu otwarte żródłowe (Nouveau, nie opracowany przez NVIDIA)

##### Sterownik graficzny
##### Mesa
###### Jest to przydatne dla wszystkich procesorów graficznych
```markdown
# pacman -S mesa lib32-mesa
```
  
<details>
<summary>INTEL</summary>
  
```markdown
# pacman -S xf86-video-intel 
```
###### jest sterownikiem Intela typu otwarte żródłowe (prawdopodobnie chcesz to pominąć i użyje sterownika modesetting. Więcej informacji można znaleźć na stronie wiki)
</details>
  
<details>
<summary>AMD</summary>
  
```markdown
# pacman -S xf86-video-amdgpu 
```
###### jest dla nowszych procesorów graficznych AMD
##### AMD-narzędzia
  
```markdown
# pacman -S libva-mesa-driver lib32-libva-mesa-driver mesa-vdpau lib32-mesa-vdpau libva-vdpau-driver lib32-libva-vdpau-driver amdvlk lib32-amdvlk
```
###### Zainstaluj te pakiety tylko wtedy, gdy używasz graficznego AMD
</details>
  
<details>
<summary>NOUVEAU</summary>
  
```markdown
# pacman -S xf86-video-nouveau 
```
###### to sterownik NVIDIA typu otwarte żródłowe
</details>
  
<details>
<summary>ATI</summary>
  
```markdown
# pacman -S xf86-video-ati
```
###### jest dla starszych procesorów graficznych AMD
</details>
  
<details>
<summary>VMWARE</summary>
  
```markdown
# pacman -S xf86-video-vmware
```
###### dla VirtualBox, VMWare, QEMU
</details>
  
<details>
<summary>FBDEV</summary>
  
```markdown
# pacman -S xf86-video-fbdev
```
###### dla Hyper-V
</details>
  
<details>
<summary>NVIDIA</summary>
  
```markdown
# pacman -S nvidia nvidia-lts nvidia-utils lib32-nvidia-utils libvdpau lib32-libvdpau
```
###### Zainstaluj te pakiety tylko wtedy, gdy używasz graficznego NVIDIA
</details>

##### Jeśli nie wiesz, możesz zainstalować wszystko, ale może się zdarzyć, że wewnętrzna karta graficzna jest używana, jeśli zainstalujesz dla niej sterownik
###### [Do góry](#spis-treści)
-----
#### 32. Środowisko pulpitu
##### Musisz wybrać środowisko graficzne
##### Instrukcje dotyczące plazmy KDE są testowane przeze mnie, ponieważ go używam.
##### Aby zainstalować środowisko graficzne KDE wydajemy polecenie:

<details>
<summary>Kde plasma</summary>

```markdown
# pacman -S plasma-desktop sddm
```
Menedżer wyświetlania SDDM
```markdown
# systemctl enable sddm
```
```markdown
# echo "exec startplasma-x11" > ~/.xinitrc
```
##### Uruchom GUI
##### Aby sprawdzić, czy środowisko graficzne działa, uruchom:
  
```markdown
# startx
```
##### Jeśli chcesz zainstalować dodatki:
```markdown
# pacman -S plasma-pa plasma-nm 
```
</details>
 
<details>
<summary>Gnome</summary>

```markdown
# pacman -S gnome gdm
``` 
Menedżer wyświetlania
```markdown
# systemctl enable gdm
```
```markdown
# echo "exec gnome-session" > ~/.xinitrc
```
##### Uruchom GUI
##### Aby sprawdzić, czy środowisko graficzne działa, uruchom:
  
```markdown
# startx
```
</details>
  
<details>
<summary>Mate</summary>

```markdown
# pacman -S mate lightdm lightdm-gtk-greeter
``` 
Menedżer wyświetlania 
```markdown
# systemctl enable lightdm
```
```markdown
# echo "exec mate-session" > ~/.xinitrc
```
</details>
  
<details>
<summary>Xfce</summary>

```markdown
# pacman -S 
``` 
Menedżer wyświetlania 
```markdown
# systemctl enable 
```
</details>

<details>
<summary>Cinnamon</summary>

```markdown
# pacman -S pacman -S 
``` 
Menedżer wyświetlania  
```markdown
# systemctl enable 
```
</details>
  
<details>
<summary>Enlightenment</summary>

```markdown
# pacman -S pacman -S 
``` 
Menedżer wyświetlania  
```markdown
# systemctl enable 
```
</details>
  
<details>
<summary>Deepin</summary>

```markdown
# pacman -S pacman -S 
``` 
Menedżer wyświetlania  
```markdown
# systemctl enable 
```
</details>
  
<details>
<summary>Budgie</summary>

```markdown
# pacman -S pacman -S 
``` 
Menedżer wyświetlania  
```markdown
# systemctl enable 
```
</details>
  
<details>
<summary>szczegóły</summary>

```markdown
# pacman -S pacman -S 
``` 
Menedżer wyświetlania  
```markdown
# systemctl enable 
```
</details>
  
<details>
<summary>szczegóły</summary>

```markdown
# pacman -S pacman -S 
``` 
Menedżer wyświetlania  
```markdown
# systemctl enable 
```
</details>

###### [Do góry](#spis-treści)
-----
#### 33. Dźwięk
##### Zainstaluj dźwięk dla KDE Plasma
```markdown
# pacman -S pavucontrol-qt
```
##### Zainstaluj dźwięk dla inne środowisko graficzne
```markdown
# pacman -S pavucontrol
```
##### Niektóre moduły PulseAudio nie są zawarte w pakiecie głównym i w razie potrzeby muszą być zainstalowane oddzielnie:

<details>
<summary>pulseaudio-alsa</summary>
  
```markdown
# pacman -S pulseaudio-alsa
```
###### dla PulseAudio do zarządzania ALSA
</details>
  
<details>
<summary>pulseaudio-bluetooth</summary>
  
```markdown
# pacman -S pulseaudio-bluetooth
```
###### dla wsparcia bluetooth (Bluez)
</details>
  
<details>
<summary>pulseaudio-equalizer</summary>
  
```markdown
# pacman -S pulseaudio-equalizer
```
###### do korektora graficzny (qpaeq)
</details>
 
<details>
<summary>alsa-plugins</summary>
  
```markdown
# pacman -S alsa-plugins
```
###### dodatkowe wtyczki alsa
</details>


  
  
  
###### [Do góry](#spis-treści)

  
  
  
  



