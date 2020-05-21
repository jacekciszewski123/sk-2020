## Ustawianie parametrów sieci

### Zadania

0. Z wykorzystaniem dowolnych systemów operacyjnych na których potrafisz uruchomić interpreter ``python`` oraz oprogramowania virtualbox odwzoruj poniższy schemat sieci:

![alt text][network]

[network]: ./network.png "Logo Title Text 2"

1. na 1 z komputerów zainstaluj i uruchom program ``server.py`` dostępne pod adresem ``https://github.com/jkanclerz/client-server-chat``
apk add git, instaluje bezpośrednio ze strony git clone http://github.com/jkanclerz/client-server-chat, wchodzę w katalog i uruchamiam program python3 server.py
2. na 2 z komputerów zainstaluj i uruchom program ``client.py`` dostępne pod adresem ``https://github.com/jkanclerz/client-server-chat``
apk add git, instaluje ze strony git clone https://github.com/jkanclerz/client-server-chat, wchodze w katalog i uruchamiam program client.py wraz z podaniem ip python3 client.py 192.168.10.10
3. Manipulując konfiguracją sieci na poziomie virtualbox, uruchom serwer czatu, oraz udostępnij go na wybranym porcie oraz adresie tak aby istniała możliwość połączenia przez inne osoby w obrębie pracowni. Tworze siec lokalna w vboxie, podlaczam sie do niej, ustawiam recznie ip na np eth0( tu i tu), odpalam server.py i client.py jak wyzej
4. Zainstaluj oprogramowanie serwera HTTP ``nginx`` lub innego, skonfiguruj plik index.html wg instrukcji, sprawdź dostępność strony z wykorzystaniem dowolnego klienta protokołu ``HTTP`` z różnych konfiguracji IP apk add nginx
5. Posługując się programami tj: ``netstat`` lub ``lsof`` sprawdź na jakich portach zostały uruchomione serwery czatu czy HTTP netstat -ltpn -> wyswietli co gdize na jakim porcie i co robi. Pozwala sprawdzić jaka usługa aktualnie działa/słucha itp (port 21-domyślny/port 80-nieszyfrowany/port 443-sztfrowany)

Wejściowe parametry sieci
-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
|   PC 1 |  
| IP - address  | 10.0.15.4 | |
| MASKA  | /24 (255.255.255.0) | |
|   |  | |
| PC 2  |  | |
| IP - address  | 10.0.15.6 | |
| MASKA  | /24 (255.255.255.0 )| |

Weryfikacja połączenia

Polecenie
ip addr 10.0.14.4/24 dev eth0 <-na PC1
ip addr 10.0.15.6/24 dev eth0 <-na PC2
ip addr flush eth0 <- wyczysci ustawienia

Efekt
Reczne ustawienie adresow ip na PC1 i PC2. Jednak po restarcie wszysto sie traci
```

Statyczna konfiguracja parametrów połączenia
Wejściowe parametry sieci
-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
|   PC 1 |  
| IP - address  | 192.168.10.10 | |
| MASKA  | 255.255.255.0 | |
|   |  | |
| PC 2  |  | |
| IP - address  | 192.168.10.11 | |
| MASKA  | 255.255.128.0 | |
| PC 2  |  | |
| IP - address  | 172.16.100.100 | |
| MASKA  | 255.255.0.0 | |

Weryfikacja połączenia

Polecenie

vi /etc/network/interfaces
    
edytorem vi zmieniam recznie w PC1
auto eth0
iface etho0 inet STATIC
 address 192.168.10.10
 netmask 255.255.255.0
 hostname localhost
 
 edytorem vi zmieniam recznie w PC2
auto eth0
iface etho0 inet STATIC
 address 192.168.10.11
 netmask 255.255.255.0
 hostname localhost
 

Efekt
Udało mi się ustawić statyczny adres IP i maske na interfaceie eth0 w PC1 i PC2, tak że po restarcie itp zachowają mi się wprowadzone dane

Nowa statyczna konfiguracja 

-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
|   PC 1 |  
| IP - address  |  | |
| MASKA  |  | |
|   |  | |
| PC 2  |  | |
| IP - address  |  | |
| MASKA  |  | |

Weryfikacja połączenia

Polecenie
```
```

Efekt
```
```

### Utrwalenie konfiguracji

Dlaczego? Jak? Co? :)

### Warto wiedzieć

-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
| Lokalizacja pliku z konfiguracją sieci| /etc/networl/interfaces| |
| UP -> Wyłączenie interfejsu sieciowego|ip link set eth1 up | |
| DOWN -> Włączenie interfejsu sieciowego| ip link set eth1 down| |
| Sprawdzenie obecnych parametrów | | |
| lista wszystkich interfejsów | | |
| Które interfejsy jakie porty słuchają | | |

