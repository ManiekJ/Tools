# Podstawowe komendy Linux

## Nawigacja w systemie
- `pwd` – wyświetla bieżący katalog
- `ls` – listuje pliki i katalogi w bieżącym katalogu
  - `ls -l` – lista w formacie szczegółowym
  - `ls -a` – pokazuje również ukryte pliki
- `cd <katalog>` – zmiana katalogu
  - `cd ..` – przejście do katalogu wyżej
  - `cd ~` – przejście do katalogu domowego
- `tree` – pokazuje strukturę katalogów w formie drzewa (może wymagać instalacji)

## Praca z plikami i katalogami
- `touch <plik>` – tworzy nowy pusty plik
- `mkdir <katalog>` – tworzy nowy katalog
- `rm <plik>` – usuwa plik
  - `rm -r <katalog>` – usuwa katalog i jego zawartość
- `cp <źródło> <cel>` – kopiuje plik lub katalog
  - `cp -r <źródło> <cel>` – kopiowanie katalogu rekursywnie
- `mv <źródło> <cel>` – przenosi lub zmienia nazwę pliku/katalogu

## Wyświetlanie zawartości plików
- `cat <plik>` – wyświetla zawartość pliku
- `less <plik>` – wyświetla zawartość pliku strona po stronie
- `head <plik>` – pokazuje pierwsze 10 linii pliku
- `tail <plik>` – pokazuje ostatnie 10 linii pliku
  - `tail -f <plik>` – monitoruje plik w czasie rzeczywistym

## Uprawnienia i własność
- `chmod <opcje> <plik>` – zmiana uprawnień pliku/katalogu
  - np. `chmod 755 <plik>` – ustawienia rwxr-xr-x
- `chown <użytkownik>:<grupa> <plik>` – zmiana właściciela i grupy
- `ls -l` – pokazuje uprawnienia, właściciela i grupę

## Procesy i zarządzanie systemem
- `ps` – pokazuje działające procesy
- `top` – monitorowanie procesów w czasie rzeczywistym
- `htop` – bardziej rozbudowany top (może wymagać instalacji)
- `kill <PID>` – zabija proces o podanym PID
- `killall <nazwa_procesu>` – zabija wszystkie procesy o danej nazwie

## Zarządzanie pakietami (Debian/Ubuntu)
- `sudo apt update` – aktualizacja listy pakietów
- `sudo apt upgrade` – aktualizacja zainstalowanych pakietów
- `sudo apt install <pakiet>` – instalacja pakietu
- `sudo apt remove <pakiet>` – usunięcie pakietu

## Zarządzanie pakietami (RedHat/CentOS/Fedora)
- `sudo yum install <pakiet>` – instalacja pakietu
- `sudo yum remove <pakiet>` – usunięcie pakietu
- `sudo yum update` – aktualizacja systemu

## Sieć i połączenia
- `ping <adres>` – sprawdza połączenie z hostem
- `ifconfig` – pokazuje konfigurację sieciową (może wymagać `net-tools`)
- `ip addr` – nowsza alternatywa dla ifconfig
- `wget <url>` – pobiera plik z internetu
- `curl <url>` – pobiera lub wysyła dane do serwera

## Szukanie plików i tekstu
- `find <ścieżka> -name <nazwa>` – wyszukiwanie plików
- `grep <wzorzec> <plik>` – wyszukiwanie tekstu w pliku
  - `grep -r <wzorzec> <katalog>` – wyszukiwanie w katalogu rekursywnie

## Archiwizacja i kompresja
- `tar -cvf <archiwum.tar> <pliki>` – tworzenie archiwum tar
- `tar -xvf <archiwum.tar>` – rozpakowywanie archiwum tar
- `tar -czvf <archiwum.tar.gz> <pliki>` – tworzenie archiwum tar.gz
- `tar -xzvf <archiwum.tar.gz>` – rozpakowywanie tar.gz
- `zip <archiwum.zip> <pliki>` – tworzenie archiwum zip
- `unzip <archiwum.zip>` – rozpakowywanie zip

## Informacje o systemie
- `uname -a` – informacje o systemie
- `df -h` – informacje o wolnym miejscu na dyskach
- `du -h <plik/katalog>` – rozmiar pliku/katalogu
- `free -h` – informacje o pamięci RAM

## Inne przydatne
- `history` – pokazuje historię komend
- `alias <nazwa>='<komenda>'` – tworzy alias komendy
- `man <komenda>` – pokazuje manual komendy
- `echo <tekst>` – wyświetla tekst w terminalu
- `clear` – czyści ekran terminala
