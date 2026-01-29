# Buffer Overflow – OVERFLOW1 (TryHackMe)

Repozytorium dokumentuje **szczegółowy przebieg realizacji zadania Task 2 – OVERFLOW1**
z platformy **TryHackMe (OSCP BOF Prep)**.

Celem repozytorium jest pokazanie **krok po kroku** procesu identyfikacji
i eksploatacji podatności typu **Buffer Overflow** w aplikacji działającej
na systemie Windows.


## Zakres projektu

Projekt obejmuje:
- pełny opis przebiegu pracy,
- wykorzystane narzędzia i środowisko,
- kolejne etapy analizy podatności,


## Środowisko testowe

- Platforma: **TryHackMe**
- Maszyna: **OSCP BOF Prep**
- System ofiary: Windows
- System atakujący: Kali Linux
- Debugger: Immunity Debugger
- Framework: Mona
- Język: Python


## Przebieg realizacji zadania

### 1. Przygotowanie środowiska
- połączenie z TryHackMe przez OpenVPN,
- uruchomienie maszyny OSCP BOF Prep,
- połączenie z maszyną przez RDP,
- uruchomienie aplikacji `oscp.exe` w Immunity Debugger.


### 2. Weryfikacja działania aplikacji
- potwierdzenie nasłuchiwania aplikacji na porcie 1337,
- test komunikacji z Kali Linux (`nc`),
- wykonanie polecenia `OVERFLOW1 test`.


### 3. Konfiguracja Mona
- ustawienie katalogu roboczego Mona,
- przygotowanie środowiska do dalszej analizy.



### 4. Fuzzing
- stworzenie skryptu `fuzzer.py`,
- wysyłanie rosnącej liczby bajtów do aplikacji,
- identyfikacja momentu awarii aplikacji.


### 5. Crash replication i kontrola EIP
- wygenerowanie wzorca cyklicznego,
- określenie dokładnego offsetu,
- potwierdzenie nadpisania rejestru EIP.


### 6. Identyfikacja bad characters
- wygenerowanie pełnej tablicy bajtów,
- porównanie pamięci z użyciem Mona,
- iteracyjne usuwanie nieprawidłowych znaków.


### 7. Znalezienie punktu skoku
- wyszukanie instrukcji `JMP ESP`,
- wybór adresu bez bad characters,
- aktualizacja exploita.


### 8. Generowanie payloadu
- wygenerowanie shellcode z użyciem `msfvenom`,
- osadzenie payloadu w exploicie,
- zastosowanie NOP sled.



### 9. Próba eksploatacji
- uruchomienie listenera netcat,
- wysłanie payloadu,
- próba uzyskania reverse shell.



## Wnioski

- Buffer Overflow jest podatnością wymagającą precyzyjnej analizy pamięci.
- Każdy etap (offset, badchars, JMP ESP) ma kluczowe znaczenie.
- Dokumentowanie procesu pozwala lepiej zrozumieć mechanizm działania exploita.


## Autor

- Emilia Zaręba


## Informacja

Repozytorium ma charakter **edukacyjny** i dokumentuje pracę wykonaną
w kontrolowanym środowisku laboratoryjnym TryHackMe.
