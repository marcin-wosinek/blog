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

## Wy?
* kto korzysta z frameworków js?
 * backbone?
 * ember?
* kto uważa że pisanie testów jest konieczne w dobrym rzemiośle programistycznym?
* kto uważa że jak pisać kod i testy to w TDD?
* kto stosuje TDD przy pisaniu przeglądarkowego js?

## Temat
* zmiany w myśleniu o front endzie
* konieczność dostosowania praktyki do nowych realiów
* przykład frameworku odpowiadającego nowym potrzebą

## Nowa rzeczywistość
* Js się rozwija 

## Tradycyjna architektura stron
* generowanie html po stronie serwera
* przesyłanie danych razem ze znacznikami html

## Podejście aplikacyjne
* wiecej logiki po stronie front endu
* tempaty jsowe

## Komunikacja z backendem
* wysyłanie requestów restowych 
* odbieranie danych w Json

## Wyzwania 
* zmiana słownika - mniej atrybutów, tagów i klas, a wiecej modeli należących do domeny aplikacji (klienci, produktu etc.)
* nowe wymagania w stosunku do jakości - wzrost ilość i znaczenia kodu realizowanego w przeglądarce

## Testowalność
* w tradycyjnym jQuerowym kodzie bardzo niska
* jeśli logika dotyka DOM - w testach będziemy musieli mockować DOM

## Boilerplate
* Kod powtarzany dla każdego kontrolera - słuchanie eventów, aktualizowanie dom etc.
* Zamiast DRY - WET (We Enjoy Typing)

## AngularJs
* framework aplikacji
* 29KB zminimalizowany i spakowany
 * backbone: 19KB (z underscore & backbone)
 * backbone: 32KB (z lodash & jQuery)
 * ember: 49KB
* brak zależności:
 * może używać jQuery, o ile jest dostępne przy uruchomieniu

## Architektura MV*
* początkowo MVC, wyewoluowało do MVVM
* w skrócie - to czym zamuje sie logika, determinuje gdzie powinna się znajdować

## Kontrolery
* wiąże 'swój' widok z resztą aplikacji
* zawiera prostą logikę, związaną z samym wyświetlaniem
(slajd zawierający mockup strony z podpisanymi kontrolerami)

## $scope
* obiekt wiążący kontroler z widokiem
* $scope.title będzie dostępny jako {{title}} w widoku

## Proste obiekty js
* pracujemy na prostych funkcjach i obiektach js
(slajd z Backbone.model.extend({}) emberem, batmanemen i czystym kodem angulara)

## Directives
* niestandardowe tagi i atrybuty zdefiniowane przez angulara, lub developera aplikacji
* rozszeżają działanie html o nowe feature
* do nich należy manipulacja DOMem
* ng-model - wiąże elementy formularza z modelem
* ng-repeat - pozwala interować po tablicach zdefiniowanych na $scope

### Prezentacja
1. Angularowe 'Hello world'
2. Templatkowanie z ng-repeat

## Filtry
* pozwalają na wygodne zarządzanie tym co jest wyświetlane w ng-repeat
* usprawniają tworzeni zawęrzającego się wyszukiwania, sortowania

## Two ways binding
* model jest jedynym źródłem prawdy
* zmiany na modelu aktualizują widok
* zmiany w widoku aktualizują model

## Wsparcie dla formularza
* rozumie atrybuty należącę html5 - required, pattern, date
* automatycznie dodaje klasy opisujące stan elementu do wprowadzania danych

### Prezentacja
1. przykład walidującego się formularza - zmiana kolorów kontrolek
2. Rzut oka na kod

## Wstrzykiwanie zależności
* nasz komponent ma przekazywane jego zależności jak parametry do funkcji go opakowywującej
* ładna definiacji powiązań między komponentami
* zwiększa testowalność

## Serwisy
* reużywalne kawałki kodu
* wstrzykiwane do kontrolerów, directives i innych serwisów
* większość logiki aplikacji powinna być w nich realizowana

## Ścieżki - $routeProvider
* dla aplikacji możemy zdefiniować ścieżki (z argumentami), przekierowania etc.
* ładnie współpracuje z przyciskami dalej i wstecz
* wspiera adresy z /# i bez

## Komunikacja z backendem - $resource
* serwis do generowani api komuniujacego się po restcie
* zalecany sposób użycia: $resource -> serwis opakowujący model -> kontroler
(slajd ze sposobem użycia)

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

### Prezentacja
1. Utworzenie aplikacji angularowej w nowym folderze
2. Odpalenie serwer i otworzenie strony w przeglądarce
3. Dodanie ścieżki do aplikacji i otworzenie w przeglądarce
4. Zmiana widoku i automatyczne odświerzenie strony

## Karma (Testacular)
* test runner pozwalający uruchamiać testy w przeglądarkach
* uruchamiamy serwer na maszynie na której tworzymy kod
* łaczymy z nim przeglądarki i serwer odpala w nich testy

### Prezentacja
1. Dodanie przycisku do widoku
2. Dodanie testu sprawdzającego czy alert został włączony
3. Napisanie kodu przechodzącego test

## Gotchas - pisanie directives
* Narzędzie na który jest opartę bardzo wiele corowych featurów frameworka - 2 ways binding
* rough developer experience - w szególności na tle bardzo gładkiej współpracy z resztą frameworka

## Gotchas - minimalizowanie kodu
* wiązanie $scopu w kontrolerze i w widoku odbywa sie po nazwach atrybutów - wymagana jest odpowiednia konfiguracja
* wstrzykiwanie zależności jest zależne od nazwy argumentu funkcji - potrzebne dodatkowe zdefiniowanie zależności

## Gotchas - $resource
* istnieje w osobnym pliku, który trzeba załadować
* zwraca puste obiektu lub tablice które będa dopiero uzupełnione po odebraniu odpowiedzi
* w zwiazku z tym musimy odraz zadeklarować czy mowa jest o tablicy czy obiekcie

## Gotchas - filtry działają tylko na tablicach
* ng-repeat przeinteruje po obiekcie - ale filtry nie bedą działać

## Gotchas - e2e testing
* skonfigurowanie testów jest skomplikowane
* może w porywach być uznane za feature pułapkę

## Gotchas - akualizowanie scope z poza frameworka
* wiekszość zmian modelu odbywa się we frameworku:
 * pobranie danych z $resource
 * jest odpalane za pomocą directives: ng-model, ng-clic
* w sytuacji użycia zmian przychodzących z poza angularowego świata może być konieczne wywołanie fukncji $digest

## Gotchas - $ w nazwach serwisów
* odróżnia serwisy frameworkowe od aplikacyjnych
* używanie $ w nazwach własnych serwisów pozbawia $ sensu

## Pytania
1. Czemu angular a nie backbone?
2. Czy to podejścia da się zintegrować z legacy code?
3. Co walidatory na html dostosowany do angulara?
4. Z jakim backendem używać angulara?

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
