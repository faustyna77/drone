Raport z realizacji projektu do koła naukowego MECHATRON

			Tytuł projektu:
Dron z kontrolerem lotu BetaFlight


	             Autor:
Faustyna Misiura 119041 Informatyka 4 rok 

























Spis treści
Wykaz części 
Schematy połączeń kontrolera lotu z silnikami oraz odbiornika z kontrolerem lotu
Parowanie odbiornika z nadajnikiem
Ustawienia nadajnika RC 

Konfiguracja ustawień w BetaFlight

Konfiguracja nadajnika w BetaFlight i testy w BetaFlight 
Proces uzbrajania drona 
Podsumowanie





















Wykaz części



Kontroler lotu BetaFlight 



odbiornik  FS-IA6B 4.0-8.4V/DC 2.4GHz 6 channel receiver



3. Nadajnik flysky FS-i6 AFHDS 2A (2.4GHz) 













4. Akumulator 2200mAh



5. Śmigła 



   

Ponadto szkielet drona z silnikami BLDC oraz podstawki (opcjonalne do lepszego startu):


silniki BLDC:





2. Schematy połączeń kontrolera lotu z silnikami


Kontroler lotu odpowiada z nadanie odpowiedniej prędkości silnikom dlatego przewody koloru białego wychodzące z ESC zostały podłączone do gniazda na kontrolerze lotu oznaczonego na rys.1 


Rys.1 złącze do linii sygnałów sterujących PWM  z ESC( Electronic Speed Controller)  połączonych z BLDC  


na rys.2 jest pokazane to złącze bez wpiętych przewodów białych z ESC (odpowiedzialnych za prędkość sterowania silnikami przez kontroler lotu):

rys.2 - widok na puste złącze do którego zostały przylutowane przewody 


Kolejnym krokiem było przylutowanie przewodu  z odbiornika w kontroler (w jeden z padów kontrolera ) celem komunikacji samego kontrolera z odbiornikiem 
Na rys3 zaznaczono punkty padów odpowiedzialne za komunikacje z odbiornikiem 
 
Rys.3 Oznaczenie punktów połączenia z odbiornikiem

Na rys.3 odpowiednio zostały oznaczone pady:
1-R2
2-4V5
3-GND
 
przylutowano do tych padów przewody wychodzące z odbiornika oznaczone kolorami
1- fioletowy
2-niebieski
3-czarny


na rys.4 zostały poglądowo te numerki zaznaczone:

Rys.4 - zaznaczone miejsca lutowania przewodów z odbiornika 


Rys.5 zawiera  poglądowe zdjęcie

Rys.5 Oznaczenia wyprowadzeń 


1-fioletowy-R2
2-niebieski-4V5
3-czarny -G (GND)



Rys.6 oznaczenia wyprowadzeń przewodów 




Pad oznaczony na kontrolerze jako R2 jest kluczowy gdyż pózniej przy konfiguracji w BetaFlight Configurator będzie należało go zaznaczyć jako pad na, którym jest komunikacja (przesył danych z odbiornika do kontrolera lotu)

Zasilanie części logicznej (ESC) silników BLDC


silniki BLDC są zamocowane na sztywno do drona ( to znaczy że ich przewody nie były ulegać modyfikacji, przez co mają z góry określony kierunek obrotu) Silniki w dronie kręciły się w następujący sposób pokazany na rys. 7 

Rys.7 zaznaczenie kierunków obrotu silników 


ESC mają wbudowany BEC (ang. Battery Eliminator Circuit - obniża napięcie z 12V do 5V) w związku z tym da się je zasilić (część logiczną odpowiedzialną za sterowanie) z 5V , ponieważ silniki BLDC mają osobne zasilanie, które wynosi 12V ESC z BEC na wyjściu (przewód czerwony (VCC)) ma 5V , aby zasilić kontroler lotu podłączono przewód wychodzący z ESC (którego napięcie z BEC ma 5V ) do jednego z padów na kontrolerze lotu (5V), przewód ten na kontrolerze został przylutowany do padu 5V dzięki temu kontroler jest zasilany z 5V z BEC ESC  gdy do silników podpięty jest akumulator 12V 
, warto wspomnieć że żeby silniki BLDC pracowały będąc sterowane przez kontroler wystarczyło podpiąc jeden przewód VCC z ESC , a pozostałe GND wychodzące z ESC spiąć wspólna masą (GND) spiętą w złączke do kontrolera. 

Na rys.8 oznaczono pad 5V do, którego podpięto vcc z BEC : 

Rys.8 zasilanie BEC [5V] do kontrolera dzięki temu kontroler jest zasilany jednocześnie wtedy gdy do silników wpięte jest zasilanie 12V z akumulatora


3.Parowanie odbiornika z nadajnikiem


Proces parowania odbiornika z nadajnikiem jest ustawiany tylko na samym początku konfiguracji w przypadku późniejszych połączeń odbiornik (po włączeniu) sam paruje się z nadajnikiem (po jego włączeniu)
niesparowany odbiornik miga, natomiast sparowany świeci ciągłym światłem 
(rys. 9) 

Rys.9 Sparowany odbiornik świeci ciągłym światłem (bez migania) 


Poniżej został przedstawiony proces pierwszego parowania ważne jest to żeby odbiornik był kompatybilny z nadajnikiem i działał na tym samym protokole komunikacyjnym w przeciwnym wypadku nigdy ich się nie uda sparować. W moim wypadku odbiornik to: 
FS-IA6B 4.0-8.4V/DC 2.4GHz, a nadajnik to:

flysky FS-i6 AFHDS 2A (2.4GHz), z czego bardzo ważne jest oznaczenie 2A, gdyż starsze nadajniki występują pod tą sama nazwa ale bez 2A i nie są one kompatybilne z odbiornikami z serii: 
FS-IA6B 4.0-8.4V/DC 2.4GHz


Proces:
Podłączenie odbiornika , włączenie do zasilania oraz ewentualnie zwarcie zworka (dołączona w zestawie do odbiornika)
włączenie nadajnika w następujący sposób -przytrzymując podczas włączania przycisk bind znajdujący się na nim (rys. 10)

Rys.10 - bind przycisk


po pomyślnym zbindowaniu (uruchamia sie na wyswietlaczu napis binding….) odbiornik powinien przestac migac i świecić ciągłym światłem 
po podłączeniu kontrolera lotu do laptopa z programem BetaFlight Configurator w zakładce z nadajnikiem, wartości roll, pitch itd powinny zaczac sie zmieniac gdy na nadajniku zaczyna się zmieniać pozycje drążków (zmiany następują w czasie rzeczywistym) -rys.11



Rys.11 - pozycja drążków 






4. Ustawienia nadajnika RC 
W moim wypadku niewiele musiałam zmieniac w ustawieniach nadajnika poniewaz sparował sie od razu bez problemu z odbiornikiem i poprawnie przekazywał sygnał z drążków w aplikacji BetaFlight , , oto poprawne i najważniejsze ustawienia : 
Konfiguracja kanałów:
Standardowe przypisanie:
CH1 - Aileron (Roll)
CH2 - Elevator (Pitch)
CH3 - Throttle (Gaz)
CH4 - Rudder (Yaw)
CH5 - ARM switch (zbrojenie)
CH6 - Flight modes
CH7-8 - Dodatkowe funkcje

ponadto lewy drążek odpowiedzialny za gaz czyli poruszanie sie drona w górę lub w dół, prawy - Pitch (góra/dół) + Roll (lewo/prawo)












Bardzo ważne jest żeby w ustawieniach nadajnika sprawdzić przypisanie poszczególnych AUX oraz drążków ponieważ później w betaFlight będą potrzebne do uzbrajania i rozbrajania drona






Konfiguracja ustawień w BetaFlight


Na poszczególnych zrzutach ekranu zostały przedstawione zaznaczone konfiguracje w poszczególnych zakładkach  BetaFlight Configuration, wazne jest zeby po zaznaczonych zmianach kliknąć ‘zapisz’ wtedy zmiany sa aplikowane do kontrolera lotu BetaFlight po uprzednim jego podłączeniu przez USB do laptopa z zainstalowanym oprogramowaniem







Najpierw tak jak na powyższym zrzucie trzeba podłączyć usb z kontrolera lotu do usb portu laptopa i połączyć się z kontrolerem w programie BetaFlight


Po połączeniu się w pierwszej zakładce powinien być widoczny dron, gdy zacznę zmieniać fizycznie pozycje kontrolera lotu , dron w aplikacji  powinien się równocześnie zacząć ruszać (w czasie rzeczywistym ) , należy ustawić kontroler lotu na dronie tak aby przy siedzeniu na prostym podłożu wskazywany kąt w aplikacji też był 0 stopni i taką konfiguracje akcelerometru zapisać , jest to bardzo istotne gdyż jeśli źle zapiszemy  pozycję drona , dron później w trakcie lotu bedzie odnosił sie do “fałszywej” pozycji i w wyniku czego będzie latał krzywo






W kolejnej zakładce wybieramy kanał R2 gdyż do tego padu na kontrolerze lotu R2 był przylutowany przewód wychodzący z odbiornika , jest to równie istotne gdyż jeśli wskażemy inny kanał np. R3 gdzie nie ma fizycznie przylutowanego przewodu z odbiornika , odbiornik nie będzie w ogóle przesyłał danych z nadajnika do kontrolera lotu i przez to nie będzie realizowane sterowanie. 


tutaj zaznaczyłam wszystkie ‘udogodnienia’ jakie daje kontroler lotu betaflight 



tutaj sa widoczne ważne ustawienia odnośnie np. utraty komunikacji odbiornika z nadajnikiem , wyczerpania baterii i innych sytuacji awaryjnych itp. 




















6.Konfiguracja nadajnika w BetaFlight i testy w BetaFlight 
Po pozytywnym zbindowaniu nadajnika z odbiornikiem , gdy stany drążków będą zmieniany lub nie tylko drążków ale też pojedynczych przełączników kanałów aux jakie występują na nadajniku , po zmianach winny być widoczne zmiany w tej zakładce , wtedy znaczy to że zarówno nadajnik jest dobrze skonfigurowany jak i odbiornik jest z nim połączony i co najważniejsze przesyła te dane o położeniu drążka i aux do kontrolera (bez opóźnień i w czasie rzeczywistym ) , kontroler z kolei przesyła je przez usb do programu beta flight configuration 





ważne jest ustawienie minimalnej i maksymalnej pozycji drążków bo względem niej będzie ustawiana prędkość silników , maksymalna pozycja drążka to prędkość maksymalna , minimalna pozycja 1000
pozycja od, której dron zaczyna się uzbrajać to 1050, pozycja środkowa to 1500, pozycja maksymalna 2000  


gdy np. zmieniłam pozycje drążka lewego tzw. drążka gazu zmieniło sie to zaraz w throttle 




7.Proces uzbrajania drona 
Uzbrajanie drona jest to stan drona w, którym jest on w stanie ruszyć do lotu, jest to stan w, którym przełączniki na nadajniku są w takiej pozycji, w, której można 
zezwolić dronowi na ruch silników w bezpieczny sposób czyli np gdy przypadkowo użytkownik da od razu pełen gaz ale nie uzbroi drona dodatkowo przełącznikiem (w moim wypadku aux5) to dron nie ruszy gwałtownie z maksymalna predkoscia bo może to spowodowac wypadek.
przełącznik odpowiedzialny za uzbrojenie drona do lotu to aux5 : 

Przełacznik AUX5 został zadeklarowany w programie z przedziałem w, którym dron ma zostac uzbrojony 

to znaczy, ze dron zacznie się uzbrajać od prędkości 1075 ( minimalna wynosi 1000) będzie sie to objawiało tym, że dron ruszy najpierw z minimalna predkoscia, a pozniej drążkami bedzie można konfigurować prędkość i ruch drona 







Po udanym uzbrajaniu można przejść do testów, zrzuty ekranu prezentowane wyżej reprezentują zakładkę związana z silnikami, betaflight configuration umożliwia przetestowanie silników bezpośrednio z aplikacji jak i po uzbrojeniu z nadajnikiem wysterowaniu silników poprzez nadajnik, ważne jest aby ustawić PWM jako protokół oraz częstotliwość PWM silników - 480 gdyż przy innych protokołach nadajnik nie powodował sterowania silnikami 

8.Podsumowanie
https://youtube.com/shorts/JuuFHdS2Jc8?feature=share

link do filmu, można zauważyć na nim jak w wyniku wykonywania poszczególnych manewrów z nadajnika zmieniają się prędkości silników BLDC oraz fragment uzbrajania i rozbrajania drona 

