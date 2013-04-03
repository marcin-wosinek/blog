---
layout: default
category: prezentacja
title: AngularJs 4developers Warszawa
tags: [AngularJs, 4developers, Warszawa]
---
# AngularJs
## Kim jestem?
* Marcin Wosinek
* 5 lat doświadczenia w IT
 * Pracy w C# zawdzięczam mocne przekonanie do testów jednostkowych
 * Pracy we front endzie - js
* aktualnie js kontraktor w Poznaniu
(legalne zdjecia z Poznania - wikipedia?)

## Wy?
* kto korzysta z frameworków js?
 * backbone?
 * ember?
* kto uważa że pisanie testów jest konieczne w dobrym rzemiośle programistycznym?
* kto uważa że jak pisać kod i testy to w TDD?
* kto stosuje TDD przy pisaniu przeglądarkowego js?
(Legalne zdjecie z publicznością)

## Temat
* zmiany w myśleniu o front endzie
* konieczność dostosowania praktyki do nowych realiów
* przykład frameworku odpowiadającego nowym potrzebą
(?)

## Nowa rzeczywistość
* Js się rozwija 
* jQuery to nie wszystko
(loga technologii jsowych - node, ember, karma, backbone)

## Tradycyjna architektura stron
* generowanie html po stronie serwera
* przesyłanie danych razem ze znacznikami html
(schemat z serwerem przesyłającym html na request)

## Podejście aplikacyjne
* wiecej logiki po stronie front endu
* templaty jsowe
(logo mustacha, handlebara i angulara)

## Komunikacja z backendem
* wysyłanie requestów restowych 
* odbieranie danych w Json
(przykład jsona)

## Wyzwania 
* zmiana słownika - mniej atrybutów, tagów i klas, a wiecej modeli należących do domeny aplikacji (klienci, produktu etc.)
* nowe wymagania w stosunku do jakości - wzrost ilość i znaczenia kodu realizowanego w przeglądarce
(?)

## Testowalność
* w tradycyjnym jQuerowym kodzie bardzo niska
* jeśli logika dotyka DOM - w testach będziemy musieli mockować DOM
(przykład kodu grzebiącego w DOM)

## Boilerplate
* Kod powtarzany dla każdego kontrolera - słuchanie eventów, aktualizowanie dom etc.
* Zamiast DRY - WET (We Enjoy Typing)
(krótki boilerplace backbona)

## AngularJs
* framework aplikacji
* 29KB zminimalizowany i spakowany
 * backbone: 19KB (z underscore & backbone)
 * backbone: 32KB (z lodash & jQuery)
 * ember: 49KB
* brak zależności:
 * może używać jQuery, o ile jest dostępne przy uruchomieniu
(logo angulara)

## Architektura MV*
* początkowo przypominała MVC, teraz bardziej MVVM - nazywan MVW(hatever) przez twórców
* w skrócie - to czym zamuje sie logika, determinuje gdzie powinna się znajdować
(?)

## Widok
* oparty o zwykły html
* wyświetla wartości w \{\{ model \}\}
* jest rozszeżony przez framework
(przykład krótkiego html z ng-model i ng-repeat)

## Kontrolery
* wiąże 'swój' widok z resztą aplikacji
* zawiera prostą logikę, związaną z samym wyświetlaniem
(slajd zawierający mockup strony z podpisanymi kontrolerami)

## $scope
* obiekt wiążący kontroler z widokiem
* $scope.title będzie dostępny jako {{title}} w widoku
* ng-model - wiąże elementy formularza z modelem
* ng-repeat - pozwala interować po tablicach zdefiniowanych na $scope
(Obrazek z wyjaśniemie co to jest scope)

### Prezentacja
1. Angularowe 'Hello world'
2. Templatkowanie z ng-repeat

## Proste obiekty js
* pracujemy na prostych funkcjach i obiektach js
(slajd z Backbone.model.extend({}) emberem, batmanemen i czystym kodem angulara)

## Filtry
* pozwalają na wygodne zarządzanie tym co jest wyświetlane w ng-repeat
* usprawniają tworzeni zawęrzającego się wyszukiwania, sortowania
(przykład z zastosowaniem filter i orderby)

## Two ways binding
* model jest jedynym źródłem prawdy
* zmiany na modelu aktualizują widok
* zmiany w widoku aktualizują model
(two ways binding z angulara)

## Wsparcie dla formularza
* rozumie atrybuty należącę html5 - required, pattern, date
* automatycznie dodaje klasy opisujące stan elementu do wprowadzania danych
(html przetworzony przez angulara)

### Prezentacja
1. przykład walidującego się formularza - zmiana kolorów kontrolek
2. Rzut oka na kod

## Wstrzykiwanie zależności
* nasz komponent ma przekazywane jego zależności jak parametry do funkcji go opakowywującej
* ładna definiacji powiązań między komponentami
* zwiększa testowalność
(kontroler z kilkoma wstrzykniętymi seriwiami - $scope, $log, $window)

## Serwisy
* reużywalne kawałki kodu
* wstrzykiwane do kontrolerów, directives i innych serwisów
* większość logiki aplikacji powinna być w nich realizowana
(prosty serwis - opakowanie dla webstorage)

## Ścieżki - $routeProvider
* dla aplikacji możemy zdefiniować ścieżki (z argumentami), przekierowania etc.
* ładnie współpracuje z przyciskami dalej i wstecz
* wspiera adresy z /# i bez
(przykład rejestracji kilku ścieżek)

## Komunikacja z backendem - $resource
* serwis do generowani api komuniujacego się po restcie
* zalecany sposób użycia: $resource -> serwis opakowujący model -> kontroler
(slajd ze sposobem użycia)

## Directives
* niestandardowe tagi i atrybuty zdefiniowane przez angulara, lub developera aplikacji
* rozszeżają działanie html o nowe feature
* do nich należy manipulacja DOMem
(wiecej directivsów)

## Yeoman (yo, grunt + bower)
* Zestaw narzędzi usprawniających workflow developerski
* yo - generatory kodu:
 * dla angulara automatyzuje tworzenie:
  * serwisów
  * directives
  * kontrolerów
  * ścieżek - kotrolera wraz z widokiem i ścieżką dostępu
 * wspiera również inne frameworki i czystego js
* grunt - automatyzacja częstych zadań
 * minimalizacja i paczkowanie kodu
 * serwer developerski z automatycznym odświeżaniem otwartej strony
* bower - zarządzanie zależnościami
(trzy loga)

### Prezentacja
1. Utworzenie aplikacji angularowej w nowym folderze
2. Odpalenie serwer i otworzenie strony w przeglądarce
3. Dodanie ścieżki do aplikacji i otworzenie w przeglądarce
4. Zmiana widoku i automatyczne odświerzenie strony

## Karma (Testacular)
* test runner pozwalający uruchamiać testy w przeglądarkach
* uruchamiamy serwer na maszynie na której tworzymy kod
* łaczymy z nim przeglądarki i serwer odpala w nich testy
(karma logo)

### Prezentacja
1. Dodanie przycisku do widoku
2. Dodanie testu sprawdzającego czy alert został włączony
3. Napisanie kodu przechodzącego test

## Gotchas - pisanie directives
* Narzędzie na który jest opartę bardzo wiele corowych featurów frameworka - 2 ways binding
* rough developer experience - w szególności na tle bardzo gładkiej współpracy z resztą frameworka
(przykład najprostrzej directives)

## Gotchas - minimalizowanie kodu
* wiązanie $scopu w kontrolerze i w widoku odbywa sie po nazwach atrybutów - wymagana jest odpowiednia konfiguracja minimalizacji
* wstrzykiwanie zależności jest zależne od nazwy argumentu funkcji - potrzebne dodatkowe zdefiniowanie zależności
(Przykład kodów - przed i po minimalizacji)

## Gotchas - $resource
* istnieje w osobnym pliku, który trzeba załadować
* zwraca puste obiektu lub tablice które będa dopiero uzupełnione po odebraniu odpowiedzi
* w zwiazku z tym musimy odraz zadeklarować czy mowa jest o tablicy czy obiekcie
(screen z firebuga z odpytaniem resourca i dostaniem pustego obiektu)

## Gotchas - filtry działają tylko na tablicach
* ng-repeat przeinteruje po obiekcie - ale filtry nie bedą działać
(Przykład filtru)

## Gotchas - e2e testing
* skonfigurowanie testów jest skomplikowane
* może w porywach być uznane za feature pułapkę
(screen z e2e testu?)

## Gotchas - akualizowanie scope z poza frameworka
* wiekszość zmian modelu odbywa się we frameworku:
 * pobranie danych z $resource
 * jest odpalane za pomocą directives: ng-model, ng-clic
* w sytuacji użycia zmian przychodzących z poza angularowego świata może być konieczne wywołanie fukncji $digest
(przykład kodu z użyciem directive)

## Gotchas - $ w nazwach serwisów
* odróżnia serwisy frameworkowe od aplikacyjnych
* używanie $ w nazwach własnych serwisów pozbawia $ sensu
(lista serwisów angularowchy, przykładowa lista naszych serwisów)

## Pytania
1. Czemu angular a nie backbone?
2. Czy to podejścia da się zintegrować z legacy code?
3. Co walidatory na html dostosowany do angulara?
4. Z jakim backendem używać angulara?
(znak zpytania)

## Materiały
* http://angularjs.org/
* http://egghead.io/
* http://www.youtube.com/user/angularjs

## Podsumowanie
* koncepcje znane z backendowych techologi będą zadomowiać sie w js
* AngularJs jest narzedziem pozwalającym na bardzo dojrzałe programowanie we front endzie
* Warto zapoznać się z yeomanem

## Kontakt
* namiary na bloga
* marcin.wosinek@gmail.com

## Podziękowania
