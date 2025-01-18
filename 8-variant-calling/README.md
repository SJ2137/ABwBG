**Raport z Variant-calling**

### Wprowadzenie

**Variant calling** to proces identyfikacji zmian w sekwencjach DNA - tzw. wariantów, poprzez porównanie odczytów sekwencyjnych genomu badanego z genomem referencyjnym. Warianty te obejmują m.in. insercje, delecje, czy zamianę pojedynczych nukleotydów, ale też zmiany strukturalne np. zmiany liczby kopii fragmentów DNA, przeniesienie fragmentu DNA między chromosomami, czy odwrócenie orientacji fragmentu DNA w obrębie chromosomu. Variant calling jest kluczowym etapem w badaniach genomowych, ponieważ pozwala na:
- zrozumienie genetycznych podstaw chorób;
- identyfikację mutacji odpowiedzialnych za cechy fenotypowe;
- analizę różnorodności genetycznej w populacjach;
- badania ewolucyjne.

Proces ten jest szczególnie ważny w medycynie precyzyjnej, gdzie wiedza o wariantach może ułatwić dobór terapii dopasowanej do konkretnego pacjenta.

### 1. Instalacja i ładowanie pakietów

Na początku kodu instalowane i ładowane są pakiety niezbędne do analizy danych genomowych:
- `VariantTools`: do analizy wariantów;
- `Rsamtools`: do przetwarzania plików BAM i FASTA;
- `GenomicRanges`: do operacji na zakresach genomowych;
- `GenomicFeatures`: do zarządzania cechami genomu;
- `VariantAnnotation`: do pracy z adnotacjami wariantów;
- `BiocParallel`: do obsługi równoległości w analizie.

### 2. Konfiguracja środowiska pracy

Ustawiany jest katalog roboczy za pomocą `setwd`, co pozwala na wygodne zarządzanie plikami wejściowymi i wyjściowymi. Funkcja `list.files()` sprawdza, jakie pliki są dostępne w bieżącym katalogu.

### 3. Wczytanie danych wejściowych

#### 3.1 Plik BAM
Plik BAM (`aligned_sample1.BAM`) jest wczytywany za pomocą funkcji `BamFile()`. Jest to skompresowany format zawierający wyrównane odczyty sekwencyjne.

#### 3.2 Genom referencyjny
Plik FASTA (`ecoli_reference1.fasta`) zawierający sekwencję genomu referencyjnego E.coli jest wczytywany za pomocą `FaFile()`.

### 4. Sortowanie i indeksowanie plików BAM oraz FASTA

#### 4.1 Sortowanie plików BAM
Plik BAM jest sortowany według współrzędnych za pomocą `sortBam()`. Sortowanie jest kluczowe dla efektywnego indeksowania i analizy danych.

#### 4.2 Indeksowanie plików FASTA i BAM
Indeksowanie plików FASTA (`indexFa()`) i BAM (`indexBam()`) pozwala na szybki dostęp do danych w trakcie analizy.

### 5. Kontrola jakości danych sekwencyjnych

Kontrola jakości danych sekwencyjnych jest kluczowa, aby upewnić się, że analiza wariantów opiera się na wiarygodnych i kompletnych danych.

#### 5.1 Nagłówek pliku BAM
`scanBamHeader()` odczytuje metadane pliku BAM, co pozwala zweryfikować strukturę i poprawność pliku.

#### 5.2 Statystyki indeksów BAM
`idxstatsBam()` generuje podstawowe statystyki, takie jak liczba wyrównań przypadających na poszczególne sekwencje w genomie.\
Liczba odczytów zmapowanych: 713927\
Liczba odczytó niezmapowanych: 506059\
Oznacza to, że 713927 odczytów zostało poprawnie przypisanych do sekwencji referencyjnej, 506059 nie zostało przypisane do żadnej pozycji w genomie referencyjnym.

#### 5.3 Pokrycie genomu
Funkcja `coverage()` oblicza liczbę odczytów przypadających na każdą pozycję w genomie.\
Funkcja `plot(coverage_data)` pozwala na wizualizację pokrycia genomu badanego z genomem referencyjnym.\
Większość pozycji w genomie ma umiarkowane pokrycie (ok. 100 odczytów).\
Regiony z bardzo wysokim pokryciem mogą wskazywać na artefakty techniczne PCR lub sekwencje powtarzalne.\
Regiony z bardzo niskim pokryciem mogą wskazywać na problemy techniczne w sekwencjonowaniu, obszary trudne do wyrównania, potencjalnie utracone fragmenty DNA.

### 6. Wykrywanie wariantów

Wykrywanie wariantów jest sercem analizy genomowej. Na podstawie danych odczytów porównywanych z genomem referencyjnym identyfikowane są pozycje, w których występują zmiany.

#### 6.1 Pileup
Funkcja `pileup()` generuje dane dotyczące liczby odczytów dla każdej pozycji w genomie. Parametr `PileupParam` określa minimalną jakość bazy (20) i to, że analiza ignoruje podział na nici DNA. W ten sposób uzyskujemy surowe dane o liczbie nukleotydów w każdej pozycji genomu.

#### 6.2 Konwersja wyników do ramki danych
Wyniki pileup są przekształcane na ramkę danych i przetwarzane za pomocą pakietu `dplyr`. Dodawane są informacje o nazwach sekwencji (`seqnames`) i danych referencyjnych. 

#### 6.3 Obliczanie prawdopodobnych wariantów
Prawdopodobne warianty są identyfikowane na podstawie liczby odczytów dla każdego nukleotydu. Wprowadzone filtry minimalnej liczby odczytów (5) oraz proporcji odczytów alternatywnych (≥ 20%) pozwalają odrzucić potencjalne artefakty sekwencjonowania lub szumy techniczne.

### 7. Filtracja i eksport wyników

Filtracja wariantów to krok, który zapewnia, że w wynikach pozostają jedynie wiarygodne warianty. Kryteria filtrowania obejmują:
- Liczbę odczytów dla danej pozycji (≥ 10).
- Proporcję odczytów alternatywnych (≥ 20%).

Ten etap jest kluczowy, aby usunąć błędne pozytywy, a zarazem zachować warianty o wysokim znaczeniu biologicznym.

#### Eksport wyników
Przefiltrowane warianty są zapisywane do pliku CSV, co pozwala na ich dalszą analizę w narzędziach zewnętrznych, takich jak Excel czy dedykowane oprogramowanie bioinformatyczne.

### Podsumowanie
Kod wykonuje kompleksową analizę wariantów genetycznych, obejmującą:
1. Wczytanie i wstępną obróbkę danych (sortowanie i indeksowanie).
2. Analizę jakości danych (pokrycie genomu, statystyki BAM).
3. Wykrywanie wariantów za pomocą pileup.
4. Filtrację prawdopodobnych wariantów na podstawie jakości.
5. Eksport wyników do pliku CSV.

Kod jest zaprojektowany do pracy z danymi genomowymi Prokaryota, a zastosowane kryteria filtracji zapewniają wysoką jakość wyników.

