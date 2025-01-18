# Raport z analizy GWAS (Genome-Wide Association Study)

## Wprowadzenie

**GWAS (Genome-Wide Association Study)** to badanie, które pozwala na identyfikację powiązań między wariantami genetycznymi (głównie SNP – single nucleotide polymorphisms) a cechami fenotypowymi, takimi jak podatność na choroby, cechy fizyczne czy reakcje na leczenie. GWAS jest szeroko stosowany w genomice roślinnej, medycynie oraz w analizie różnorodności genetycznej.

Badanie GWAS pozwala na:
- zrozumienie podstaw genetycznych chorób lub cech fenotypowych;
- wykrywanie genów związanych z danym zjawiskiem;
- identyfikowanie biomarkerów, które mogą być użyteczne w diagnostyce lub doborze terapii.

Dzięki GWAS możliwe jest znalezienie nowych markerów genetycznych, które mogą wskazywać na potencjalne cele terapeutyczne.

---

## 1. Instalacja i ładowanie pakietów

Na początku kodu instalowane i ładowane są pakiety wymagane do analizy danych genotypowych:
- `rrBLUP`: do analizy związków między genotypami a fenotypami;
- `BGLR`: do zaawansowanej analizy genotypów;
- `SNPRelate`: do analizy i manipulacji danymi SNP;
- `dplyr`: do manipulacji danymi;
- `qqman`: do wizualizacji wyników GWAS;
- `poolr`: do analizy statystycznej i obliczeń na danych genotypowych.

---

## 2. Wczytanie danych genotypowych i fenotypowych

Wczytanie danych z plików `.ped`, `.fam` i `.map`, które zawierają odpowiednio dane genotypowe, informacje o próbkach oraz mapowanie markerów SNP. Te dane są następnie analizowane pod kątem ich spójności i poprawności.

---

## 3. Przekodowanie wartości markerów

Na tym etapie wartości markerów są przekształcane do postaci, która będzie odpowiednia do analizy.
- Wartość 2 została przekodowana na `NA` (brakujące dane).
- Wartość 0 została przekodowana na `0` (homozygota dla allelu głównego).
- Wartość 1 została przekodowana na `1` (heterozygota).
- Wartość 3 została przekodowana na `2` (homozygota dla allelu mniejszościowego).

---

## 4. Konwersja danych do macierzy

Dane genotypowe zostały przekonwertowane na macierz, co pozwala na ich dalszą analizę w bardziej wygodnej formie. Dane zostały również przetransponowane, aby były odpowiednio uporządkowane pod kątem analizy.\
Wymiary macierzy: 413 (liczba osobników), 36901 (liczba markerów SNP).

---

## 5. Wczytanie danych fenotypowych

Dane fenotypowe zawierające cechy fenotypowe próbek zostały wczytane i sprawdzone pod kątem zgodności z danymi genotypowymi (TRUE). Identyfikatory próbek zostały przypisane do wierszy macierzy danych genotypowych, aby zapewnić odpowiednią zgodność.

---

## 6. Kontrola jakości (QC) danych markerowych

Na tym etapie dokonano kontroli jakości danych markerowych.\
Wartości `NA` w danych markerów zostały zastąpione średnią wartością dla danego markera.\
Wymiary nowej macierzy: 374, 36542.\
Po przefiltrowaniu markerów (MAP1), usunięto te, które miały niską różnorodność genetyczną (MAF < 5%). Przeprowadzona filtracja ma na celu poprawienie jakości danych, ponieważ markery o niskiej częstości allelu mniejszościowego mogą prowadzić do fałszywych wyników w analizach GWAS.\
W wyniku tego procesu zmniejszyła się liczba markerów SNP (z 36901 do 36542).

---

## 7. Analiza PCA

Wykonano analizę głównych składowych (PCA), aby zbadać różnorodność genotypową próbek. Analiza ta pozwala na ocenę struktury populacji i wykrycie ewentualnych błędów w danych.\
Wyniki PCA zostały zwizualizowane na wykresach, które przedstawiają rozkład próbek na dwóch pierwszych głównych składowych.\
Widoczne są trzy ugrupowania punktów znajdujących się bardzo blisko siebie, co oznacza trzy grupy podobne genetycznie, ale jednocześnie różniące się miedzy sobą (ze względu na rozmieszczenie w różnych miejscach wykresu).

---

## 8. Przygotowanie danych do GWAS

Dane genotypowe i fenotypowe zostały przygotowane do analizy GWAS.
- Dane genotypowe zostały zorganizowane w formie tabeli, która zawiera informacje o markerach SNP.
- Dane fenotypowe zostały zorganizowane, tak aby odpowiadały odpowiednim próbkom.

---

## 9. Przeprowadzenie analizy GWAS

Została przeprowadzona analiza GWAS, aby znaleźć związki między wariantami genotypowymi a cechami fenotypowymi. Proces ten pozwala na identyfikację markerów SNP, które są statystycznie powiązane z analizowaną cechą.

---

## 10. Wyodrębnienie istotnych markerów SNP

Po przeprowadzeniu analizy GWAS, wyodrębniono markery SNP, które wykazały statystycznie istotne powiązania z cechą fenotypową.\
Wynik: 10 markerów znajdujących się w chromosomach: 1, 2, 3, 6, 7 i 12.\

Filtracja wyników opierała się na kryteriach p-value (y < 1e-04), co pozwalało na identyfikację najistotniejszych markerów.\
Wyniki po filtracji: 6 markerów znajdujących się w chromosomie 1.

---

## 11. Stworzenie wykresu Manhattan

Na końcu stworzono wykres Manhattan, który wizualizuje wyniki analizy GWAS. Wykres ten przedstawia rozmieszczenie markerów SNP na chromosomach, a jego celem jest zobrazowanie obszarów genomu, które wykazują silne powiązania z analizowaną cechą.

---

## Podsumowanie

Analiza GWAS została przeprowadzona w celu zidentyfikowania markerów genetycznych powiązanych z cechami fenotypowymi. Raport obejmuje następujące etapy:
1. Wczytanie i wstępna obróbka danych genotypowych oraz fenotypowych.
2. Kontrola jakości danych markerów SNP.
3. Analiza PCA.
4. Przygotowanie danych do analizy GWAS.
5. Przeprowadzenie analizy GWAS.
6. Wyodrębnienie istotnych markerów SNP.
7. Stworzenie wykresu Manhattan w celu wizualizacji wyników.

