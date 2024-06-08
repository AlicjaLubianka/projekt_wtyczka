# Wtyczka QGIS
## Opis
Wtyczka oferuje możliwość wykonania następujących operacji w programie QGIS :

--> **Dla dwóch punktów**:
- obliczenie różnicy wysokości,
- obliczenie odległości,
- wyznaczenie azymutu oraz azymutu odwrotnego.

--> **Dla trzech albo więcej punktów**:
- obliczenie pola powierzchni,
- stworzenie nowej warstwy z poligonem.

--> **Dodatkowe możliwości programu**:
- zliczanie zaznaczonych punktów,
- wczytywanie pliku ze współrzędnymi punktów w układzie współrzędnych płaskich prostokątncyh PL-1992 lub PL-2000,
- czyszczenie wyników,
- odznaczanie wszystkich zaznaczonych punktów.

--> **Program pozwala również na zmianę jednostek dla wszystkich obliczeń**:
- różnica wysokości: *metry [m], centymetry [cm], milimetry [mm],*
- odległość: *metry [m], kilometry [km],*
- azymut oraz azymut odwrotny: *radiany [rad], stopnie [deg], grady [g],*
- pole powierzchni: *metry kwadratowe [m2], ary [a], hektary [ha].*


## Wymagania
- Python 3.11.5
- Biblioteki: math, PyQt5
- QGIS 3.34.7

## System operacyjny
Program został napisany dla systemu operacyjnego Windows 11.

## Instrukcja obsługi
Program umożliwia wykonywanie wymienionych operacji w określonej wersji QGIS. 
Poniżej znajduje się opis funkcji każdego przycisku oraz instrukcja dotycząca wczytywania pliku.

--> **Pole wyboru "Aktualna warstwa":**
- To pole pozwala wybrać warstwę, na której będą wykonywane operacje za pomocą naszej wtyczki.

--> **Licz elementy:**
- Po naciśnięciu tego przycisku program zwraca liczbę zaznaczonych elementów.

--> **Różnica wysokości:**
- Przycisk jest przeznaczony dla punktów z atrybutem wysokości oznaczonym jako **"h"**. Po naciśnięciu przycisku, po jego prawej stronie program wyświetla różnicę wysokości między zaznaczonymi punktami w metrach *[m]*. Po prawej stronie okna pojawiają się również trzy przyciski umożliwiające zmianę jednostki wyniku. Po wybraniu jednej z nich program pokaże wynik w odpowiedniej jednostce, gdzie: *[m] - metry, [cm] - centymetry, [mm] - milimetry.*

--> **Pole powierzchni:**
- Po naciśnięciu tego przycisku, po jego prawej stronie, program wyświetli pole powierzchni obszaru utworzonego przez zaznaczone punkty w metrach kwadratowych *[m2]*. Dodatkowo, po prawej stronie okna, pojawią się przyciski umożliwiające zmianę jednostki wyświetlanego wyniku. Po wybraniu jednej z opcji, program wyświetli wynik w wybranej jednostce: *[m2] - metry kwadratowe, [ha] - hektary, [a] - ary.*

--> **Odległość:**
- Po naciśnięciu tego przycisku, z jego prawej strony wyświetlona zostanie odległość między zaznaczonymi punktami w metrach. Dodatkowo, po prawej stronie okna, pojawią się przyciski umożliwiające zmianę jednostki wyniku. Po wyborze odpowiedniego przycisku, program pokaże wynik w wybranej jednostce: *[m] - metry, [km] - kilometry.*

--> **Azymut**
- Po naciśnięciu przycisku, z jego prawej strony wyświetlona zostanie wartość azymutu między zaznaczonymi punktami w radianach. Po prawej stronie okna pojawią się przyciski do zmiany jednostki wyniku. Po wybraniu odpowiedniego przycisku, program wyświetli wynik w jednej z wybranych jednostek: *[g] - grady, [deg] - stopnie, [rad] - radiany.*

- Pod wyświetlonym wynikiem pojawi się przycisk "Azymut odwrotny". Po jego naciśnięciu, w miejscu przycisku pojawi się wartość azymutu odwrotnego, a sam przycisk zniknie. Przy zmianie jednostki wyniku za pomocą przycisków radiowych, obie wartości - azymut i azymut odwrotny - zostaną przedstawione w wybranej jednostce.

--> **Rysuj poligon**
- Ten przycisk dodaje nową warstwę z narysowanym poligonem łączącym zaznaczone punkty.

--> **Wyczyść wyniki**
- Po naciśnięciu tego przycisku wszystkie wyświetlane wyniki zostaną usunięte. Również wszelkie komunikaty o wynikach lub błędach, wyświetlane w górnej części interfejsu QGIS, zostaną usunięte.

--> **Odznacz wszystko**
- Przycisk ten odznacza wszystkie zaznaczone punkty.

--> **Wczytaj plik**
- Przycisk ten służy do wczytywania plików .txt lub .csv zawierających współrzędne punktów. Współrzędne powinny być zapisane w pliku w taki sposób, że każda para współrzędnych X,Y jest umieszczona w nowym wierszu, a separator dziesiętny to kropka, natomiast współrzędne X i Y oddziela przecinek. Przykład dla układu PL-2000:

6505557.947008692,5698134.984363967  
6494228.235143422,5698070.40673962  
6495892.9210715005,5700279.960207025  
6503651.900047439,5699120.895453971  
6495434.756193247,5699114.967959793  
6495761.020010711,5700346.070648875  

Po naciśnięciu przycisku pojawi się okno dialogowe, w którym należy wybrać układ współrzędnych. Po wyborze układu, wyświetli się okno umożliwiające wybór pliku z dowolnego miejsca na urządzeniu. 

**1.** Dla układu PL-2000: po wyborze pliku program zapyta o strefę, w której znajdują się wprowadzone punkty. Po wyborze jednej z czterech dostępnych stref (strefa 5, strefa 6, strefa 7, strefa 8), program załaduje i wyświetli punkty na nowo utworzonej warstwie.

**2.** Dla układu PL-1992: po wybraniu pliku program załaduje punkty i wyświetli je na nowo utworzonej warstwie. 


## Znane błędy i nietypowe zachowania
- Jeśli użytkownik wybierze opcję **"Różnica wysokości"** lub **"Odległość"** lub **"Azymut"** mając zaznaczoną **inną ilość punktów niż 2**, program wyświetli komunikat na dole okna: **"Zaznacz dokładnie 2 punkty!"**
  
- W przypadku, gdy punkty wybrane przez użytkownika do obliczenia różnicy wysokości nie mają atrybutu wysokości, program wyświetli ostrzeżenie w głównym interfejsie QGIS, a także komunikat na dole okna: **"Wybrane punkty nie mają atrybutu wysokości."**

- Gdy użytkownik wybierze dwa punkty o takich samych współrzędnych i skorzysta z opcji **"Azymut"**, program wyświetli komunikat na dole okna: **"Punkty są identyczne!"**

- Przy korzystaniu z opcji **"Pole powierzchni"**, jeśli są zaznaczone **mniej niż 3 punkty**, program wyświetli komunikat na dole okna: **"Zaznacz więcej punktów."**

- Podobnie, przy użyciu funkcji **"Rysuj poligon"**, jeśli zaznaczonych **jest mniej niż 3 punkty**, program wyświetli komunikat na dole okna: **"Za mało punktów."**

- Jeśli po naciśnięciu przycisku **"Rysuj poligon"** pojawi się jeden z błędów:

	**"Nieprawidłowa geometria poligonu",**  
	**"Nie udało się utworzyć warstwy poligonowej"**,  
	**"Nie udało się dodać funkcji do warstwy poligonowej"**,  
   oznacza to, że utworzenie poligonu z wybranych punktów jest prawdopodobnie niemożliwe.

- W przypadku użycia funkcji **"Wczytaj plik"** dla pliku z **więcej niż dwiema kolumnami danych lub z błędnie oddzielonymi współrzędnymi**, program wyświetli ostrzeżenie w głównym interfejsie QGIS: **"Wybrany plik ma więcej niż 2 kolumny danych."**

- Jeśli podczas próby wczytania pliku z danymi za pomocą **"Wczytaj plik"** pojawi się komunikat błędu konwersji w głównym interfejsie QGIS: **"Wystąpił błąd podczas konwersji współrzędnych."**, należy spróbować ponownie wczytać plik lub sprawdzić, czy ma on poprawną formę.




