# Raport z analizy adnotacji waraintów

## Wprowadzenie

Pakiet VariantAnnotation w genomice jest używany do adnotacji wariantów genetycznych, czyli przypisywania dodatkowych informacji do zidentyfikowanych wariantów DNA (np. mutacji, delecji, insercji). Umożliwia to lepsze zrozumienie biologicznych skutków tych wariantów i ich potencjalnych powiązań z chorobami, cechami fenotypowymi czy funkcjami biologicznymi.

Do głównych zastosowań pakietu VariantAnnotation w genomice należą:
- adnotacja wariantów
- analiza konsekwencji biologicznych (np. zmiany struktury białka, zaburzenia w transkrypcji)
- korelacja z bazami danych
- ocena istotności wariantów

## 1. Instalacja i ładowanie pakietów

Na początku zainstalowano i załadowano pakiety niezbędne do wykonania analizy:

- `VariantAnnotation`
- `GenomicRanges`
- `AnnotationHub`

## 2. Wczytanie i eksploracja danych

Za pomocą funkcji `readVcf` wczytano przykładowy plik VCF z pakietu `VariantAnnotation`, następnie poprzez wywołanie funkcji `vcf` wyświetlono podstawowe informacje o zawartości pliku, takie jak:
- nagłówki pliku
- pozycja w genomie
- genotypy
- typ danych (string/ float)

## 3. Analiza jakości

 Za pomocą funkcji `summary(qual(vcf))` wykonano analizę jakości, która dostarczyła informacji takich jak:
 - minimum
 - maximum
 - średnia
 - mediana
 - 1 i 3 kwartyl
 - ilość pustych obserwacji

## 4. Filtrowanie wariantów

Funkcja `vcf[!is.na(qual(vcf)) & qual(vcf) >99, ]` pozwoliła na odfiltrowanie wariantów, gdzie:

- `!is.na(qual(vcf))` zapewnia, że nie są brane pod uwagę warianty z brakującymi wartościami jakości
- `qual(vcf) > 99` zapewnia, że są brane pod uwagę tylko warianty o bardzo wysokiej jakości (powyżej 99)

## 5. Anotacja wariantów

  Przeprowadzono anotację wariantów za pomocą funkcji `locateVariants` z ddoatkowym wykorzystaniem pakietu anotacyjnego `TxDb.Hsapiens.UCSC.hg19.knownGene` w celu wzbogacenia wariantów o informacje genowe.

 Funkcja`locateVariants` pozwala na identyfikację pozycji w genomie, w których występują zmiany w stosunku do genomu referencyjnego, a także czy warianty znajdują się w regionach kodujących białka, czy w innych ważnych obszarach.

Przykładowe zastosowanie:

- Lokalizowanie SNP w regionach kodujących białka
- Analiza wpływu wariantów na geny
- Adnotacja wariantów z danymi zewnętrznymi

## Podsumowanie

W ramach analizy przeprowadzono następujące kroki:

- wczytanie i zapoznanie się z danymi typu VCF
- analiza jakości wczytanych plików
- filtrowanie wariantów, w celu pozostawienia tylko tych o bardzo wysokiej jakości
- anotacja wariantów z wykorzystaniem pakietu anotacyjnego `TxDb`


