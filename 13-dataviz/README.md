# Wykorzystanie wykresów do wizualizacji danych genomowych
## 1. Wykresy podstawowe:

### 1a. **Boxplot** - przedstawianie rozkładu zmiennych oraz identyfikacji potencjalnych odchyleń (tzw. outlierów)
W **genomice** można go zastosować do:
- wykazywania różnic w poziomie ekspresji genów między różnymi próbkami
- przedstawienia rozkładu wartości genotypowych w odniesieniu do fenotypu w badaniach SNP i GWAS

### 1b. **Histogram** - przedstawianie rozkładu częstotliwości wartości danej zmiennej
W **genomice** można go zastosować do:
- wizualizacji rozkładu liczby SNP w genomie
- wizualizacji rozkładu częstości alleli w populacji w badaniach GWAS
- analizy jakości danych z sekwencjonowania (np. przedstawienie rozkładu głębokości pokrycia)

### 1c. **Scatter plot** - przedstawienie relacji między dwiema zmiennymi
W **genomice** można go zastosować do:
- przedstawienia asocjacji pomiędzy wariantami genetycznymi (np. SNP) a fenotypem
- wizualizacja zależności między ekspresją dwóch różnych genów w wielu próbkach
- przedstawienie próbek w przestrzeni, co pozwala na ich grupowanie próbek na podstawie podobieństw genetycznych lub różnic w ekspresji genów

### 1d. **Violin + Boxplot** - taką hybrydę wykresów stosuje się aby dostarczyć bardziej szczegółowych informacji o rozkładzie danych
W **genomice** można go zastosować do:
- pokazania jak różne genotypy wpływają na rozkład fenotypów w badaniach SNP

## 2. Wykres Stacked Bar Plot (skumulowane słupki) - przedstawienie proporcji różnych kategorii w danej grupie, pokazując sumaryczną wartość i rozkład poszczególnych komponentów
W **genomice** można go zastosować do:
- analizy proporcji genotypów w populacji
- porównanie częstości alleli w różnych grupach badanych

## 3. Waffle Plot - wizualizacja proporcji w zbiorach danych
W **genomice** można go zastosować do:
- występowanie poszczególnych alleli w populacji
- określenia występowania różnych typów mutacji w genomie

## 4. Time Series Plot (analiza czasowa) - wizualizacja zmian wartości różnych parametrów w różnych punktach czasowych
W **genomice** można go zastosować do:
- śledzenia zmiany poziomu ekspresji genów
- monitorowanie zmiany częstości występowania alleli w populacji

## 5. Waterfall Plot - przedstawienie skumulowanych zmian wartości kolejnych zmiennych w sposób kaskadowy
W **genomice** można go zastosować do:
- przedstawienia różnych mutacji w różnych genach
- wizualizacja odpowiedzi organizmu na leczenie

## 6. Volcano Plot - umożliwia łatwą identyfikację najbardziej znaczących i biologicznie istotnych wyników
W **genomice** można go zastosować do:
- wizualizacji wyników różnicowej analizy metylacji DNA
- identyfikacji SNP-ów, które są najbardziej związane z określonymi cechami fenotypowymi

## 7. Heatmap - prezentuje wartości w macierzy danych za pomocą kolorów
W **genomice** można go zastosować do:
- przedstawienia wyników różnicowej ekspresji genów
- porównanie wielu SNP-ów i ich wpływu na różne fenotypy

# 8a. PCA - przekształcenie dużego zbioru skorelowanych zmiennych w mniejszy zestaw nieskorelowanych zmiennych
W **genomice** można go zastosować do:
- wizualizacji różnic między próbkami na podstawie ich profilu ekspresji genów
- rozpoznania grup populacji genetycznych lub zidentyfikowania potencjalnych strukturalnych cech genetycznych w danych SNP

## 8b. t-SNE - przekształcenie wysokowymiarowych danych w przestrzeń o niższym wymiarze, zazwyczaj dwuwymiarową (2D) lub trójwymiarową (3D), przy jednoczesnym zachowaniu lokalnych relacji między danymi
W **genomice** można go zastosować do:
- redukcji wymiarowości danych SNP w badaniach asocjacyjnych (GWAS), co pomaga w wizualizacji zależności genetycznych między próbkami
-  identyfikacji i wizualizacji różnic między różnymi typami lub stanami komórek

**PCA** działa lepiej w przypadku linearności danych, **t-SNE** z kolei sprawdza się w przypadku złożonych, nieliniowych zależności.

## 9. Manhattan Plot - specjalny rodzaj wykresu punktowego, który jest szeroko stosowany w badaniach GWAS w celu wizualizacji wyników testów statystycznych związanych z zależnościami między markerami genetycznymi, a cechami fenotypowymi
W **genomice** można go zastosować do:
- pokazuje SNP-y rozmieszczone wzdłuż chromosomów, co pozwala zrozumieć, czy istotne asocjacje są rozproszone po całym genomie
- reprezentacja regionów genomowych, w których SNP-y są istotnie związane z daną cechą

## 10a. Diagram Venna - przedstawienie zbiorów danych i ich części wspólnych oraz różnic
W **genomice** można go zastosować do:
- wizualizacji porównań zestawów genów
- porównywania zestawów SNP-ów związanych z różnymi cechami lub chorobami

## 10b. UpSet Plot - alternatywa dla tradycyjnego diagramu Venna, która pozwala na bardziej przejrzystą wizualizację nakładania się dużych zestawów danych
Jest **bardziej funkcjonalny** niż diagram Venna w sytuacjach, gdy mamy do czynienia z dużymi i złożonymi zbiorami danych, takimi jak porównania genów, SNP-ów czy wyników transkryptomicznych.

## 11. Pathway and Annotation Plots (na przykładzie **KEGG**) - przedstawianie złożonych interakcji biologicznych w kontekście szlaków metabolicznych, sygnalizacyjnych i funkcjonalnych
Jednym z najczęściej stosowanych narzędzi do tego typu analiz jest baza KEGG, która dostarcza gotowe do użycia diagramy szlaków biologicznych.
W **genomice** można go zastosować do:
- wizualizacji, w jaki sposób różne geny lub produkty genów uczestniczą w specyficznych szlakach biologicznych

## 12. Drzewo filogenetyczne - graficzna reprezentacja ewolucyjnych relacji pomiędzy różnymi gatunkami, organizmami, genami, lub białkami
W **genomice** można go zastosować do:
- identyfikacji, jak geny zmieniały się w czasie i jakie relacje mają między sobą w kontekście ewolucyjnym
- identyfikacji homologii

## 13. Synteny Plots (na przykładzie **genoPlotR**) - wizualizacja względnej pozycji genów w chromosomach pomiędzy różnymi genomami w trakcie ewolucji
W **genomice** można go zastosować do:
- wizualizacji relacji i podobieństw między genomami różnych gatunków, osobników lub szczepów
- analizy duplikacji genów

## 14. Circos Plots - przedstawienie informacji w formie okręgów, co umożliwiaja ukazanie zależności pomiędzy różnymi elementami danych
W **genomice** można go zastosować do:
- przedstawianie strukturalnych zmian w genomie, takich jak fuzje chromosomów, inwersje, translokacje czy duplikacje genów
- porównywanie genomów różnych gatunków

## 15. Ideograms (na przykładzie karyoploteR) - graficzne reprezentacje struktury chromosomów, które służą do przedstawiania układu genów, markerów, mutacji i innych istotnych elementów genomu na poziomie chromosomów
W **genomice** można go zastosować do:
- analizy lokalizacji genów
- zaznaczenie miejsc w genomie, gdzie występują mutacje
