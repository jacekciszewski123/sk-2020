## Konfiguracja route


* routing
    * dodaj trasę default -> ip route add default via (ip przez co ma iść -router-)
    * dodaj trasę przez bramę
    * dodaj trasę przez interfejs -> ip route add (ip do jakiej sieci chce iść -cała sieć- / MASKA) via (ip przez które mogę-ip routera)
    * usuń trasę ip route delete (ip/MASKA) via (ip)
    * zmień trasę -> ip replace (ip/MASKA) dev 
    * pobierz trasę dla adresu -> ip route get (ip)
    
    odblokowanie przekazywanie pakietow na kompie ktory robi jako routeR: w większości przypadków komputer, który robi za router ma orzyblokowane przekazywanie pakietów dalej
    
- echo 1 > /proc/sys/net/ipv4/ip_forward  |  echo 0 > /proc/sys/net/ipv4/ip_forward
- sysctl net.ipv4.ip_forward=1  |  sysctl net.ipv4.ip_forward=0
- żeby na stałe trzeba plik zamienić jakoś
     
### ip 
| subcommand    |  polecenie   | opis  |
| ------------- |:-------------| :---------------| 
|   ``route``    |                               | |
|               |   ``ip route add``             | |


### Zastosowania

* Wydzielenie osobnej sieci dla urządzeń sieciowych
* Separacja urządzeń gościnnej sieci WIFI do osobnej sieci
* Zapewnienie komunikacji pomiędzy odrębnymi sieciami lokalnymi z wykorzystaniem VPN

![zadanie 4](example-network.svg)

### Zadanie

![zadanie 4](cwiczenia4.svg)

1.
   * Przygotuj konfigurację sieci zgodnie z powyższym diagramem, 
   * Przetestuj połączenie pomiędzy wszystkimi elementami sieci
   * Dlaczego połączenie może nie działać
2. Przygotuj konfigurację tak aby została załadowana poprawnie po ponownym uruchomieniu systemu
   * Patrz ``utrwalanie statycznej konfiguracji cwiczenia 2``
   * zwróć uwagę na różnice pomiędzy dydtrybucjami systemu
3. Zainstaluj, uruchom i przetestuj działanie aplikacji ``chat``
   * aplikacja dostępna w serwisie github ``https://github.com/jkanclerz/client-server-chat`` lub preinstalowana na maszynie dostępnej w zasobach kursu

### Zadanie do domu

1. Przygotuj konfigurację z zadania 1 wykorzystując inny system operacyjny na komputerze pełniącym rolę routera.
  * debian / centos / inny
  * zapewnij poprawną komunikację pomiędzy PC3 -> PC1
  
2. Dodaj kolejną sieć do komputera pełniącego funkcję routera
   * Sprawdź poprawność komunikacji pomiędzy innymi obszarami sieci
   * Zweryfikuj działanie programu chat pomiędzy różnymi segmentami sieci

![zadanie 4](todo.svg)
