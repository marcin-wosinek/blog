---
layout: default
category: warsztaty
title: Warsztaty AngularJs Akai Poznań
tags: [AngularJs, Akai, Poznań]
---
# AngularJs: Warsztaty - stopień 2

## Środowisko
* konsolowy git
* chrome/chromium
 * korzystamy z `<input type="range">`
 * powinen być slider tutaj: <input type="range">

## Start (text)
* Treść slajdów: http://bit.ly/angular-workshop2
* git clone https://github.com/marcin-wosinek/workshop-2.git
* chrome:
 * linux: chromium-browser --disable-web-security
 * windows - skopiować link do chroma i edytować: "(originalny link) --disable-web-security"
* git config --global alias.tree "log --oneline --graph --decorate --all"

## Projekt (screen appki)
* Książka kontaktów
  * lista kontaktów
  * strona osoby
  * formularz edycji

## Struktura plików (screen folderów)
* app/ zawier wszystko co jest potrzebne do zdepoloyowania aplikacji
 * index.html - jedyny plik do użytku bezpośredniego
 * view/ - templaty angulara
 * styles/ - pliki css i nie skopilowany sass
 * components/ - zewnętrzne komponenty
 * scripts/ - js
  * app.js - definicja modułu + konfiguracja
* test/ katalog z testami

## Yeoman
* narzedzie do wspierania workflowu developerskiego
* generator kodu
* od następnych warsztatów będziemy z niego korzystać

### Prezentacja:
1. Generowanie ścieżki
2. Odpalenie serwera
3. Automatyczne odświerzenie na zmianę

3. pisanie filtrów
 * przypomnienie filtrów w angularze
 * TODO: Zadanie1: filtr usuwania polskich znaków
 * Zadanie2: filtr przedziału

4. Animacje
 * rys historyczny: PITA w angularze
 * mówienie aktualnego rozwiązania http://www.yearofmoo.com/2013/04/animation-in-angularjs.html
 * Demo http://www.nganimate.org/
 * Zadanie2: implementacja animacji
5. cookies
 * omówienie cookiesów
 * Narzędzia do cookiesów w angularze
 * zastosowanie ciasteczek:
  * przechowywanie danych - stara metoda
  * session id dla zalogowanego user - lepiej uzywać tej koncepcji http://witoldsz.github.io/angular-http-auth/
  * śledzenie użytkownika/liczenie UU
 * Zadanie3: tracking cookies
6. pisanie directive
 * template + ng-transclude omówienie
 * Zadanie4: directive z ogłoszeniem o ciasteczkach - guzik z akceptacją
 * linking function: dostęp do elementu - ustawieni klasy na elemencie zawierającym
 * Zadanie5: directive z ogłoszeniem o ciasteczkach - implementacja chowania
 * linking function - przechwytywanie eventów
 * Zadanie6: unselectable directive
 * izolowanie scope - demonstracja problemów:
  * @
  * =
 * Zadanie6: kontrolka dla filtru przedziału
 * demo - hack żeby nie dało się min przekroczyć max

## Instalowanie yeomana
