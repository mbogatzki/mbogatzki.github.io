# Conclusions from books

## Clean Code: A Handbook of Agile Software Craftsmanship - Robert C. Martin

###Nazwy zmiennych:
- Nie używać bardzo podobnych nazw, bo mogą być mylące.
- Unikać dużego "O" i małego "l", bo często mylone są z 0 i 1.
- Używać nazw łatwych do wymowy, aby można było rozmawiać o kodzie.
- Ustalić jedną nazwę na pojęcie i trzymać się jej.
- Używać nazwy wzorców w nazwie.
- Nie używać w nazwie przedrostków takich jak skrót nazwy projektów, bo podpowiadanie w IDE, będzie mało użyteczne.

###Funkcje:
- Ograniczyć do minimum wielkość funkcji (20 linii)
- Funkcja powinna wykonywać tylko jedną czynność (zmieniać coś lub zwracać coś) - Unix philosophy
- Funkcja powinna mieć tylko jeden poziom abstrakcji.
- Funkcje powinny być generyczne.
- Usuwać powtórzenia kodu - DRY
- Unikać efektów ubocznych.
- Rzucać wyjątek zamiast kod błędu.
- Argumenty:
  - Stosować jak najmniejszą liczbę argumentów (max. 3), bo utrudnia to testowanie (ilość kombinacji argumentów).
  - Nie używać boolean jako argument, ponieważ oznacza to, że funkcja robi dwie rzeczy.
  - Używać obiektu jako argumentu gdy trzeba przekazać więcej danych do funkcji.

###Komentarze:
- Pisać jak najmniej komentarzy i tylko wtedy gdy są niezbędne, np. ostrzeżenia lub wyjaśnienie nietypowego rozwiązania.
- Stosować komentarze TODO
- Pisać dokumentację tylko dla publicznego API, dokumentacja kodu wewnętrznego tylko go zaciemnia.
- Nie zostawiać zakomentowanego kodu.

###Czytelność:
- Używać pustego wiersza dla rozdzielenia np. deklaracji zmiennych - zwiększa to czytelność.
- Zmienne powinny być deklarowane blisko ich użycia.
- Zmienne instancyjne powinny być deklarowane na samym początku.
- Usuwać nieużywany kod.
- Używać stałych.
- Używać funkcji, zamiast długich warunków.
- Unikanie warunków negatywnych.

###Pozostałe:
- Unikać zwracania null oraz przekazywania go jako argumentu.
- Używać narzędzia do logowania.
- Nie mieszać języków w ramach jednego pliku.
- Nie mieszać poziomów abstrakcji.
- Podczas rozwijania kodu, poprawiać go.
- Budowanie projektu powinno być proste i zamykać się w 3 poleceniach:
     1. ściągnięcie repozytorium
     2. uruchomienie budowania
     3. uruchomienie testów

###Testy jednostkowe:
- Jeśli to możliwe to pisać kod w TDD.
- Często uruchamiać testy.
- Testy powinny być z taką samą jakością jak reszta kodu.
- Używać tylko jednej aseracji na test.
- Używać narzędzia do kontroli pokrycia testami.
- Zwrócić szczególną uwagę na warunki graniczne.
- F.I.R.S.T - Fast, Independent, Repeatable, Self-Validating, Timely

###"Prosty projekt":
  1. przechodzi wszystkie testy
  2. nie zawiera powtórzeń
  3. wyraża intencje programisty
  4. minimalizuje ilość klas i metod

You should also check Robert C. Martin Blog:
[The Clean Code Blog](http://blog.cleancoder.com)

---

## JavaScript Patterns - Stoyan Stefanov

###Dobre praktyki i podstawowe informacje:
- Windowanie (ang. hoisting) zmiennych oraz funkcji, czyli przeniesienie deklaracji za samą górę (do globalnego zasięgu lub do zasięgu funkcji).
- Optymalizacja pętli for przez przypisanie wartości length do zmiennej.
- Obiekty HTMLCollection (np. `documet.images`, `documet.forms`, `document.forms[0].elements`) za każdym pytaniem o length sprawdzają DOM.
- Parsowanie typu string na number `+"08"` lub `Number("08")`
- Używanie narzędzi takich jak ESLint lub JSHint, które pozwalają zadbać o jakość kodu, jak np. brakujące średniki, nawiasy wąsate, porównania za pomocą `===` czy też używanie `hasOwnProperty` w pętli `for-in`.
- Konwencja nazywania: metody prywatne z podkreśleniem na początku, "stałe" pisane wielkimi literami, konstruktory pisane z wielkiej litery.

###Funkcje
- Różnica w windowaniu (ang. hoisting) wyrażenia funkcyjnego a deklaracji funkcji polega na tym, że w przypadku deklaracji całość jest przenoszona na początek i od razu można użyć tej funkcji. Wyrażenie funkcyjne przenosi na początek tylko deklaracje, zatem odwołanie się do tej funkcji zwróci undefined.
- Wzorzec wywołania zwrotnego czyli callback - należy pamiętać działaniu `this` w wywołaniu zwrotnym. Przekazanie właściwego `this` można uzykać na kilka sposobów:
  * użycie `var that = this;`
  * użycie metody `apply()`
  * użycie funkcji strzałkowy (ang. arrow function) dostępnych w ES6
- Funkcje samo definiujące się, czyli funkcja która w pierwszym wywołaniu nadpisuje samą siebie zmieniając swoje działanie. Może to służyć np. do inicjalizacji.
- Funkcje samo wywołujące się (ang. immediately-invoked function expression) są powszechnie używane i zapobiegają zaśmiecaniu przestrzeni globalnej.
- Wzorzec zapamiętywania to sposób na przechowywanie wyników funkcji dla dany argumentów. polega on na stworzeniu w funkcji obiektu, którego kluczem jest jeden argument funkcji (lub kilka zserializowanych), a przed dokonaniem obliczeń w funkcji sprawdza się czy ten obiekt posiada już wartość dla danego argumentu, jeśli tak to zwraca się ją, a w przeciwnym wypadku dokonuje się obliczeń.
- Rozwijanie funkcji (ang. currying) to przekształcenie funkcji np. dwu argumentowej w jedno argumentową, która zwraca funkcję również jedno argumetnową. Curryingu używa się dla funkcji uruchamianych w większości z tymi samymi argumentami. Funkcja tworzy dokmnięcie wokół zwracanej funkcji z zapamiętanymi wartościami argumentów.
- Przykładowe użycie: `add(6)(9);` lub `var foo = add(6); foo(9);`

###Obiekty
- Wzorzec przestrzeni nazw polega na zdefiniowaniu pustego obiektu, którego nazwa będzie stanowić przestrzeń nazw. Każda funkcja, zmienna lub konstruktor będą częścią tego obiektu.
- Dobrą praktyką jest deklarowanie zależności. Przypisuje się zewnętrzne moduły na samym początku do zmiennych. Dzięki temu można łatwo zorientować się w zależnościach, można łatwo napisać je podczas testów jednostkowych, lecz także przeszukiwanie lokalnych zmiennych jest szybsze niż wyszukiwanie w obiekcie globalnym.
- Wzorzec modułu to również powszechnie używany sposób na tworzenie modułów. Polega on na przypisaniu do zmiennej funkcji samowykonywującej się (ang. IIFE) w której na początku deklarujemy zależności, właściwości i metody prywatne. Na końcu funkcji zwracamy obiekt z metodami dostępnymi publicznie. W IIFE możnemy również przekazać jako argument zmienne globalne.
- Wzorzec łańcucha wywołań to coś co w Clean Code nazwane pociągiem do koszmaru. Polega ona na tym, że każda metoda obiektu zwraca `this`, czyli swój obiekt. Dzięki temu możliwe jest wywołanie łańcucha w ten sposób: `jakisObiekt.metodaA().metodaB().metodaC();`

###Dziedziczenie:
- Wzorzec domyślny - przypisanie nowej instancji obiektu rodzica do właściwości `prototype` konstruktora dziecka.
- Pożyczanie konstruktora - użycie w konstruktorze dziecka konstruktora rodzica (bez `new`) z użyciem metody `call()` i argumentem `this`.
- Pożyczanie i ustawienie prototypu - połączenie dwóch powyższych metod.
- Współdzielenie prototypu - przypisanie do prototypu konstruktora dziecka, prototypu konstruktora rodzica.
- Konstruktor tymczasowy - stworzenie nowej, tymczasowej, pustej funkcji. Przypisanie do prototypu konstruktora tej funkcji prototypu konstruktora rodzica a następnie przypisanie do prototypu konstruktora dziecka nowego obiektu funkcji tymczasowej (użycie `new`).
- Prototypowe - przy użyciu `Object.create()` z ECMAScript5.
- Dziedziczenie przez kopiowanie - utworzenie nowego obiektu a następnie skopiowanie przy użyciu pętli wszystkich właściwości rodzica.
- Wzorzec wymieszania (ang. mix-in) - to samo co w dziedziczeniu przez kopiowanie, lecz nie z jednego obiektu, lecz z dowolnej ich liczby.
- Pożyczanie metod - użycie metod `call()`, `apply()` i `bind()`.

###Wzorce:
- Singleton - każdy obiekt utworzony za pomocą literału to jedyny egzemplarz danego obiektu. Przy tworzeniu obiektu za pomocą konstruktora singletona można uzyskać, poprzez zwrócenie pola `this.instance`, a gdy ono nie istnieje przypisanie do pola `this.instance` nowego egzemplarza tego obiektu a następnie zwrócenie go. Dzięki temu uzyskujemy zawsze tylko jedną instancję tego obiektu.
- Fabryka - pozwala zwrócić obiekt utworzony za pomocą innego konstruktora, w zależności od przekazanego argumentu. Można to uzyskać przez napisanie kilku różnych konstruktorów, przypisanie do wybranego (za pomocą argumentu) prototypu konstruktora nowej instancji obiektu przodka a następnie zwrócenie nowej instancji wybranego prototypu (`new Przodek[typ]();`)
- Iterator - dostarcza on metod, które pozwalają na iterowanie przez kolekcję danych w nim zawartych. Najczęściej definiuje się dwie metody: `next()` oraz `hasNext()`. Pierwsza zwraca kolejną wartość z kolekcji danych zaś metoda `hasNext()` zwraca true lub false w zależności czy w kolekcji są jeszcze jakieś dane czy nie.
- Dekorator - definiujemy konstruktor z polami np. `this.sum` oraz `this.decoratorsList` (które jest tablicą). Następnie do konstruktora dodajemy pole `decorators` będące obiektem, a do jego pól dodajemy obiekty zawierające metodę np. `add(x)`, która zwraca wynik różnych działań. Dodajemy do konstruktora także metodę `decorate`, która dodaje do `decoratorsList` wartość z argumentu. Na koniec definiujemy dekorowaną metodę `add(x)`, w której używając pętli wykonujemy wszystkie dekoratory z `decoratorsList`. Dzięki temu możemy użyć `a.decorate('z'); a.decorate('y'); a.add(x);`
- Strategia - należy zdefiniować konfiguracje - obiekt w którym zawarte jest jakie pole ma użyć jakiej metody(strategii). Następnie w polu `types` definiujemy różne strategie(obiekty) zawierające metodę o tej samej nazwie np. `validate`, lecz różnym działaniu. Główna metoda `validate` strategii sprawdza każde pole danych przekazanych w argumencie a następnie sprawdza w konfiguracji jakiej metody użyć i takiej używa.
- Fasada - to prosty pośrednik, który dostarcza interfejs dla jakiejś funkcjonalności.
- Pośrednik - jest podobny do fasady jednak pozwala np. na gromadzenie wywołań.
- Mediator - jest to sposób na unikanie bezpośredniej komunikacje między różnymi obiektami i zastąpienie jej poprzez komunikację przez obiekt mediatora.
- Obserwator - składa się z 4 elementów:
  * tablicy `subribers`,
  * metody `subscribe`, która dodaje do tablicy `subscribers`,
  * metody `unsubscribe`, która usuwa z tablicy `subscribers`,
  * metody `publish`, która przechodzi przez wszystkich subskrybentów z tablicy `subscribers` i wykonuje ich metody.

###DOM - dobre praktyki
- Unikanie dostępu do DOM w pętli.
- Przypisywanie referencji DOM do lokalnych zmiennych.
- Modyfikowanie DOM przy użyciu `createDocumentFrgament` a potem `cloneNode` a na końcu `replaceChild`.
- Używanie workerów do ciężkich obliczeń.
