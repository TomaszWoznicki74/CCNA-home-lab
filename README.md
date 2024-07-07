# Home Lab CCNA

## Opis
To repozytorium zawiera wszystkie materiały i konfiguracje związane z moim laboratorium domowym CCNA. Projekt ma na celu pomoc w nauce i przygotowaniach do egzaminu CCNA, oferując praktyczne ćwiczenia i przykłady konfiguracji sieci.

## Zawartość Repozytorium
- **Konfiguracje urządzeń**: Skrypty konfiguracji dla routerów, przełączników i innych urządzeń sieciowych.
- **Dokumentacja**: Notatki, diagramy sieciowe i inne materiały pomocne w nauce.
- **Ćwiczenia**: Przykłady i zadania do wykonania, które pomagają w opanowaniu materiału CCNA.

## Wymagania
- **Oprogramowanie**: Cisco Packet Tracer lub inne podobne narzędzie do symulacji sieci.
- **Sprzęt**: (opcjonalnie) Prawdziwe urządzenia Cisco, takie jak routery i przełączniki, jeśli dostępne.

## Jak zacząć
1. **Klonuj repozytorium**:
    ```bash
    git clone https://github.com/TwojeKonto/Home-Lab-CCNA.git
    cd Home-Lab-CCNA
    ```
2. **Otwórz projekt w Cisco Packet Tracer** lub innym narzędziu do symulacji sieci.
3. **Przejrzyj dokumentację** w celu zrozumienia topologii sieci i konfiguracji.
4. **Rozpocznij ćwiczenia** według dostarczonych instrukcji.

## Struktura Katalogów
- **/configurations**: Pliki konfiguracyjne dla różnych urządzeń sieciowych.
- **/documentation**: Notatki, diagramy i inne materiały pomocnicze.

## Przykładowa Konfiguracja
Poniżej znajduje się przykładowa konfiguracja routera:

```shell
enable
configure terminal
hostname Router1
interface GigabitEthernet0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown
exit
interface GigabitEthernet0/1
 ip address 192.168.2.1 255.255.255.0
 no shutdown
exit
router ospf 1
 network 192.168.1.0 0.0.0.255 area 0
 network 192.168.2.0 0.0.0.255 area 0
end
