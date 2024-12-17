# Rozpoznawanie emocji za pomocą sieci neuronowych

## Opis projektu

Ten projekt to aplikacja, która rozpoznaje emocje na podstawie obrazów twarzy za pomocą konwolucyjnych sieci neuronowych (CNN).  
Głównym celem jest wykorzystanie technologii głębokiego uczenia do klasyfikacji obrazów twarzy na różne emocje, takie jak radość, smutek, złość itp.

## Cel projektu

Celem projektu jest:

1. Zbudowanie modelu zdolnego do rozpoznawania emocji z obrazów twarzy.
2. Przeprowadzenie treningu modelu na zestawie danych obrazów twarzy.
3. Stworzenie aplikacji, która wykorzystuje kamerę do bieżącego rozpoznawania emocji na podstawie twarzy użytkownika.


## Dane

Zestaw danych został podzielony na dwie części:

- **Dane treningowe** znajdujące się w folderze `images/train-kopia/`.
- **Dane walidacyjne** znajdujące się w folderze `images/validation/`.

Każdy folder zawiera podkatalogi odpowiadające emocjom, np. `happy`, `sad`, `angry` itp.  
W każdym podkatalogu znajdują się obrazy twarzy odpowiadające danej emocji.

Zestaw danych pochodzi z platformy [Keggle](https://www.kaggle.com/code/jonathanoheix/face-expression-recognition-with-deep-learning/input).
Zestaw został pobrany za pomocą API.

> **Uwaga:** Aby uruchomić kamerkę na swoim komputerze, wystarczy załadować odpowiednie biblioteki oraz uruchomić wszystkie komórki z kodem po wczytaniu modelu. Natomiast jeśli chcesz samodzielnie wytrenować model, musisz pobrać dane z linku powyżej i umieścić je w folderze projektu, nie zmieniając nazwy folderu.


## Uwagi końcowe
Projekt realizowany na zajęcia Podstawy sztucznej inteligencji AGH i jest przeznaczony wyłącznie do celów edukacyjnych.
W przypadku wykorzystania zestawu danych lub aplikacji w innych celach, upewnij się, że przestrzegasz przepisów dotyczących ochrony danych osobowych i prywatności.


## GIF z wynikiem

![Wynik](pokaz-dziaania.gif)


## Podsumowanie i wnioski
Podsumowując cały projekt, był to bardzo ciekawy i wartościowy proces. Na początku podzieliłem dane na dwie opcje: trzy klasy i sześć klas. Podczas obróbki danych zauważyłem, że dane z kategorii "disgust" były zbyt ograniczone, przez co zdecydowałem się je usunąć z analizy, aby nie zaburzały modelu. Następnie, aby lepiej zrozumieć dane, wyświetliłem po trzy losowe obrazy z każdej kategorii, co pomogło mi w lepszym przygotowaniu zbioru danych.

Podczas pracy na Macu napotkałem problem z tworzeniem dodatkowego folderu DS Store, który zawierał informacje o lokalizacji plików i błędnie interpretował te pliki jako nazwy emocji. Udało się to naprawić, uwzględniając ten problem w dalszym przetwarzaniu danych.

Podczas budowy modelu postawiłem na zastosowanie kilku warstw konwolucyjnych, co przyczyniło się do znaczącej poprawy wyników. Po przeprowadzeniu testów zdecydowałem, że 40 epok to optymalna liczba, a zapisanie modelu okazało się bardzo pomocne, ponieważ znacznie przyspieszyło testowanie, eliminując konieczność ponownego generowania modelu za każdym razem.

W analizie wyników widzimy, że najlepiej rozpoznawana jest kategoria "Happy", natomiast "Fear" wypada najgorzej, głównie ze względu na podobieństwa z innymi emocjami. Z moich testów wynika, że model sprawdza się doskonale podczas rozpoznawania emocji na kamerce internetowej, co zostało potwierdzone przez dane.

Jestem bardzo zadowolony z wyników projektu i cieszę się, że mogłem zdobyć nowe doświadczenie, które przyczyniło się do mojej nauki i rozwoju.
