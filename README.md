# ConjointAnalysis_ColaBeverages
Repozytorium zawiera kod pomagający w przeprowadzeniu badania preferencji konsumentów napojów gazowanych typu cola z wykorzystaniem metody conjoint analysis

### Wstęp:
W Pythonie, analogicznie do kodu w R z wykorzystaniem biblioteki **AlgDesign**, można stworzyć cząstkowy układ czynnikowy za pomocą biblioteki **pyDOE2** oraz dodatkowych metod optymalizacji. Niestety, pyDOE2 nie posiada bezpośredniego odpowiednika funkcji `optFederov` z AlgDesign, ale można użyć innych narzędzi, takich jak `sklearn` (do optymalizacji) do redukcji profili.


---


### Wyjaśnienie kodu:
1. **Definicja poziomów**:
   - Liczba poziomów dla każdego atrybutu została określona następująco:
     - Marka: 4 poziomy (Coca-Cola, Pepsi, Marki rzemieślnicze, Marka własna supermarketu).
     - Zawartość cukru: 2 poziomy (Pełnocukrowa, Zero cukru).
     - Rodzaj opakowania: 3 poziomy (Plastikowa butelka, Puszka aluminiowa, Szklana butelka).
     - Smak: 3 poziomy (Klasyczny, Wanilia, Owocowy).

2. **Generowanie pełnego układu czynnikowego**:
   - Funkcja `fullfact()` tworzy pełny plan czynnikowy na podstawie liczby poziomów każdej zmiennej.

3. **Redukcja do cząstkowego układu**:
   - Wybieramy losowo 14 profili z pełnego układu za pomocą funkcji `np.random.choice()`. Ustawienie ziarna (`seed`) zapewnia powtarzalność wyników.

4. **Mapowanie poziomów na rzeczywiste wartości**:
   - Numeryczne wartości wygenerowane przez `fullfact()` są mapowane na ich rzeczywiste nazwy przy użyciu słownika `mappings`.

5. **Skala oceny**:
   - Respondenci mogą oceniać profile na skali od 1 (z pewnością nie wybrałabym/nie wybrałbym) do 10 (z pewnością wybrałabym/wybrałbym). Skala ta może być dodana jako kolumna w ankiecie.

6. **Zapis wyników**:
   - Wynikowy cząstkowy układ czynnikowy jest zapisany jako DataFrame i eksportowany do pliku CSV.


---


###Wynik:
   - Kod wygeneruje pełny plan czynnikowy zawierający wszystkie kombinacje atrybutów i ich poziomów. Dla podanych danych będzie to $$4 \times 2 \times 3 \times 3 = 72$$ kombinacji.
   - Kod wygeneruje cząstkowy układ czynnikowy składający się z 14 profili, które są losowo wybrane z pełnego układu. Profile będą numerowane zgodnie z ich indeksami w pełnym układzie, co odpowiada podejściu stosowanemu w AlgDesign.
