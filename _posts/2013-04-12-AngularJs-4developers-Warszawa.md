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

## Architektura MVVM

## Kontrolery

## $scope

## Walidacja formularza

### Prezentacja
1. przykład walidującego się formularza - zmiana kolorów kontrolek
2. Rzut oka na kod

## Proste obiekty js

## Two ways binding
* model jest jedynym źródłem prawdy
* zmiany na modelu aktualizują widok
* zmiany w widoku aktualizują model

## Wstrzykiwanie zależności

## Directives

## Filtry

## Serwisy

## Ścieżki - $routeProvider

## Komunikacja z backendem - $resource

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
