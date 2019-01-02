##Programowanie funkcyjne w JavaScript
Programowanie funkcyjne główny nacisk kładzie na wartościowanie (często rekurencyjnych) funkcji, a nie na wykonywanie poleceń.
W czystym programowaniu funkcyjnym, raz zdefiniowana funkcja zwraca zawsze tę samą wartość dla danych wartości argumentów, tak jak funkcje matematyczne.
Zaletami PF są zwięzłość i łatwość tworzenia programów współbieżnych z powodu m.in. braku efektów ubocznych.
  
Nieodłącznymi pojęciami związanymi z PF są m.in. rekurencja, leniwe wartościowanie (ang. lazy-evaluation) a także optymalizacja rekurencji ogonkowej (ang. tail call optimization).
  
Rekurencja w PF zastępuje pętle i wykorzystywana jest gdy wykonujemy często tą samą funkcję wiele razy, lecz z innymi parametrami.
Niestety nie wszystkie silniki JavaScript  dobrze optymalizują wywołania rekurencyjne to może doprowadzić do otrzymania błędu: `RangeError: Maximum call stack size exceeded`.
TCO (Tail Call Optimization) jest ważną częścią języków, których głównym paradygmatem jest właśnie PF jak np. Haskell czy Scheme. TCO jest częścią specyfikacji ES2015 jednak wspieranie jej nie jest jeszcze powszechne. 
Aby używać TCO w node.js od wersji 6.6.0 należy uruchomić go z flagami `--harmony --use_strict`. Jego działanie można sprawdzić wykonując poniższy kod:
```javascript
  (function f() { return f(); }())
```
Jeśli podczas wykonywania powyższego kodu nie zobaczymy komunikatu: `RangeError: Maximum call stack size exceeded` to znaczy, że TCO działa.
Niestety rekurencja posiada pewien narzut pamięciowy przez co jest wolniejsza od zwykłej pętli. Tutaj z pomocą przychodzi biblioteka [lazy.js.](http://danieltao.com/lazy.js/)
Biblioteka ta daje ogromy skok wydajnościowy, dzięki temu, że grupuje wszystkie operacje, które są do wykonania na tablicy i dopiero na końcu wykonuje iteracje po tablicy.
Nie tworzone są żadne tablice pośrednie.
  
Mówiąc o PF w JavaScript przede wszystkim wspomina się o 3 metodach wprowadzonych w Standardzie ECMA-262 języka JavaScript:
- [map](https://developer.mozilla.org/pl/docs/Web/JavaScript/Referencje/Obiekty/Array/map)
- [reduce](https://developer.mozilla.org/pl/docs/Web/JavaScript/Referencje/Obiekty/Array/Reduce)
- [filter](https://developer.mozilla.org/pl/docs/Web/JavaScript/Referencje/Obiekty/Array/filter)

Są to metody tablic, przyjmujące jako argument funkcję i zwracające nową tablicę. Nie posiadają żadnych efektów ubocznych tzn. w żaden sposób nie modyfikują tablicy na której operują. Dzięki temu, że zwracają nową tablice mogą być wywoływane w łańcuchu: `tablica.map(jakasFunkcja).filter(innaFunkcja).reduce(jeszczInnaFunkcja);`. Niestety, jak zostało wspomniane wyżej, nie jest to rozwiązanie optymalne. Każda z tych metod iteruje po całej tablicy zwróconej przez poprzednią metodę. W zamian zyskujemy tutaj brak efektów ubocznych, większą zwięzłość oraz lepszą czytelność.
  
Leniwe wartościowanie (ang. lazy evaluation) polega na wyznaczaniu wartości argumentów funkcji tylko wtedy, kiedy są potrzebne, dzięki czemu unika się dokonywania czasami ciężkich obliczeń w przypadku gdy funkcja ta nie zostanie wykonana.
  
Polecam również zapoznanie się z [tym](http://latentflip.com/loupe/?code=!!!) materiałem, który doskonale prezentuje działanie m.in. stosu w JavaScript.
