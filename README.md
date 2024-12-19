# Rozpoznawanie emocji za pomocą sieci neuronowych

## Opis projektu - wprowadzenie

Projekt polega na stworzeniu aplikacji rozpoznającej emocje na podstawie obrazów twarzy za pomocą konwolucyjnych sieci neuronowych (CNN). Głównym celem jest wykorzystanie głębokiego uczenia do klasyfikacji emocji, takich jak radość, smutek, złość i inne. Projekt ma na celu rozwój technologii, która może znaleźć zastosowanie w psychologii, interfejsach użytkownika lub systemach bezpieczeństwa.

---

## Cel projektu

- Zbudowanie modelu zdolnego do klasyfikacji emocji z obrazów twarzy.
- Przeprowadzenie treningu modelu na odpowiednim zbiorze danych.
- Stworzenie aplikacji rozpoznającej emocje w czasie rzeczywistym za pomocą kamery.

---

## Dane wejściowe

### Struktura danych
Zestaw danych podzielono na:
- **Dane treningowe**: `images/train/` (6 klas) i `images/train-kopia/` (3 klasy).
- **Dane walidacyjne**: `images/validation/`.

Każdy folder zawiera podfoldery odpowiadające emocjom, np. `happy`, `sad`, `angry`, z obrazami twarzy dla danej emocji.

Zestaw danych pochodzi z platformy [Kaggle](https://www.kaggle.com/code/jonathanoheix/face-expression-recognition-with-deep-learning/input).
Zestaw został pobrany za pomocą API.

> **Uwaga:** Aby uruchomić kamerkę na swoim komputerze, wystarczy załadować odpowiednie biblioteki oraz uruchomić wszystkie komórki z kodem po wczytaniu modelu. Natomiast jeśli chcesz samodzielnie wytrenować model, musisz pobrać dane z linku powyżej i umieścić je w folderze projektu, nie zmieniając nazwy folderu.

### Statystyki danych
- **Rozmiar obrazów**: 48x48 pikseli.
- **Liczba emocji**: 6 (bez kategorii `disgust` ze względu na brak wystarczających danych).
- **Zakres intensywności pikseli**: 0-255 (po normalizacji: 0.0-1.0).

#### Liczba obrazów w kategoriach:
| Emocja   | Liczba obrazów |
|----------|----------------|
| Happy    | 7164           |
| Sad      | 4938           |
| Fear     | 4103           |
| Surprise | 3205           |
| Neutral  | 4982           |
| Angry    | 3993           |

---

## Etap preprocessingu

Przygotowanie danych obejmowało następujące kroki:
1. **Zmiana rozmiaru obrazów**: przeskalowanie do wymiarów 48x48 pikseli – odpowiednia rozdzielczość dla CNN pozwalająca na efektywną ekstrakcję cech.
2. **Konwersja do skali szarości**: uproszczenie danych do jednokanałowych obrazów w celu zmniejszenia złożoności obliczeniowej.
3. **Normalizacja danych**: skalowanie pikseli do zakresu [0, 1] dla lepszej stabilności treningu.
4. **Usunięcie kategorii**: pominięcie `disgust`, aby poprawić jakość klasyfikacji i uniknąć problemów związanych z małą liczbą próbek.

---

## Wykorzystane metody i modele

### Architektura modelu
- **Warstwy konwolucyjne**: ekstrakcja cech obrazu.
- **Warstwy maksymalnego pooling’u**: redukcja wymiarów danych.
- **Warstwy w pełni połączone**: klasyfikacja emocji.
- **Dropout**: zapobieganie nadmiernemu dopasowaniu modelu.

### Parametry modelu
- **Optymalizator**: Adam – wybrany ze względu na efektywność w szybkim dostosowywaniu wag i dobrą wydajność w sieciach CNN.
- **Funkcja kosztu**: categorical_crossentropy – odpowiednia dla klasyfikacji wieloklasowej.
- **Liczba epok**: 40 – zapewnia odpowiednią liczbę iteracji, unikając niedouczenia oraz nadmiernego dopasowania.
- **Rozmiar batcha**: 32 – kompromis między szybkością treningu a stabilnością gradientów.
- **Funkcje aktywacji**: ReLU (ukryte warstwy), Softmax (warstwa wyjściowa).

---

## Eksperymenty

Przetestowano kilka konfiguracji:
- Model dla **3 klas emocji** (np. `happy`, `sad`, `angry`) osiągnął wysoką dokładność.
- Rozszerzenie na **6 klas** wymagało dostrojenia hiperparametrów, ale pozwoliło na lepsze wyniki ogólne.
- Przetestowano różne liczby epok oraz wielkości batchy – obecne parametry dawały najlepsze wyniki.
- Eksperymentowano także z liczbą oraz rodzajem warstw konwolucyjnych.

---

## Ocena jakości modelu

Model oceniono przy użyciu następujących metryk:
- **Dokładność (accuracy)**: 
  - Validation Loss: `1.035`
  - Validation Accuracy: `0.626`.
  Model poprawnie sklasyfikował około 62.6% obrazów w zbiorze walidacyjnym, co jest akceptowalnym wynikiem dla podstawowej architektury CNN.
- **Macierz pomyłek**: Kategorie `Sad` i `Fear` są najczęściej mylone ze względu na ich wizualne podobieństwo.

---

## Wyniki szczegółowe

### Wnioski
- Model uzyskał wysoką dokładność w kategoriach `Happy` i `Neutral`.
- Problemy z kategorią `Fear` wynikają z podobieństwa do `Sad`.
- Usunięcie kategorii `Disgust` poprawiło jakość klasyfikacji.
- Ogólnie, model osiągnął dokładność na poziomie 63%, co może wydawać się stosunkowo niskim wynikiem. Jednak w kontekście pracy z obrazami i analizy emocji na podstawie twarzy, jest to wynik uznawany za zadowalający, szczególnie w przypadku podstawowej architektury CNN.

---

## Możliwe usprawnienia

1. **Zwiększenie danych treningowych**: szczególnie dla kategorii `Fear` i `Sad`, co zwiększy dokładność modelu.
2. **Zastosowanie transfer learningu**: wykorzystanie pretrenowanych modeli, np. ResNet lub EfficientNet.
3. **Fine-tuning hiperparametrów**: optymalizacja parametrów treningowych, np. liczby warstw i ich konfiguracji.
4. **Augmentacja danych**: zwiększenie różnorodności zestawu treningowego poprzez operacje takie jak obrót, skalowanie i odwracanie obrazów.

---

## Demonstracja wyników

Aplikacja może działać w czasie rzeczywistym, analizując emocje z obrazu wideo z kamery.

![Wynik](pokaz-dziaania.gif)
