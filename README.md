# 📊 Projekt: Czy Polacy tyją szybciej niż rosną ceny?

## 👨‍🎓 Informacje o autorze
* **Imię i nazwisko:** Kamil Batorowicz
* **Przedmiot:** Eksploracyjna Analiza Danych (EDA)

## 📝 Temat i cel projektu
Celem niniejszej analizy jest zbadanie korelacji między zmianami cen poszczególnych grup towarów i usług, a trendem wzrostu wagi (otyłości) w polskim społeczeństwie w latach 1999–2022. Wykorzystując techniki eksploracyjnej analizy danych, projekt weryfikuje hipotezę o ekonomicznych uwarunkowaniach problemu otyłości.

## 💾 Źródła danych
Projekt opiera się na danych z dwóch głównych źródeł:
1. **GUS (Główny Urząd Statystyczny) - Bank Danych Lokalnych**
   * `CENY_1466_CTAB_20251210132654.csv` – średnie ceny detaliczne żywności.
   * `CENY_1473_CTAB_20251210132959.csv` – średnie ceny usług (np. fryzjer) i produktów chemicznych.
2. **NCD Risk Factor Collaboration (Lancet 2024)**
   * `NCD_RisC_Lancet_2024_BMI_age_standardised_Poland.csv` – dane dotyczące wskaźnika BMI dla osób dorosłych w Polsce z podziałem na płeć.

## 🔍 Podstawowy opis danych i preprocessing
Surowe dane wymagały odpowiedniego przygotowania przed przystąpieniem do analizy. Główne kroki przetwarzania to:
* **Parsowanie danych z GUS:** Stworzenie autorskiej funkcji `clean_gus_data` do wyodrębnienia lat, nazw produktów i cen z niestandardowo sformatowanych nagłówków plików CSV.
* **Ujednolicenie koszyków:** Złączenie kolumn reprezentujących ten sam produkt, którego gramatura uległa zmianie na przestrzeni lat (np. chleb z 0,5 kg na 0,6 kg).
* **Interpolacja braków:** Zastosowanie liniowej interpolacji w celu uzupełnienia brakujących obserwacji cenowych w poszczególnych latach.
* **Tworzenie wskaźników bazowych:** Stworzenie zagregowanych koszyków (spożywczy, chemiczny) oraz przeliczenie wartości na indeksy (gdzie rok 1999 = 100%), by móc badać procentową dynamikę zmian.

## 📈 Najciekawsze wykresy i wizualizacje
W głównym notatniku wygenerowano wykresy obrazujące kluczowe zależności (maks. 10):
1. **Wykres dynamiki cen:** Porównanie dynamiki wzrostu cen "koszyka spożywczego", usług (np. strzyżenie męskie) oraz chemii gospodarczej.
2. **Trend otyłości w Polsce:** Obraz wzrostu odsetka osób zmagających się z otyłością na przestrzeni badanych dwóch dekad.
3. **Zestawienie indeksów:** Połączony wykres liniowy obrazujący, jak indeks otyłości rośnie względem indeksu cen usług i jedzenia na wspólnej osi czasu.
4. Inne wykresy eksploracyjne analizujące poszczególne dobra (np. drób, usługi).

## 🧮 Ewentualne analizy statystyczne
Wykorzystano **Macierz Korelacji**, by sprawdzić siłę zależności zmiennych:
* Zbadano powiązania między Indeksem Otyłości, Indeksem Fryzjer (usługi), Indeksem Spożywczym i Indeksem Chemii.
* Wyniki pokazały bardzo silną korelację dodatnią (wszystkie współczynniki > 0.90, np. 0.97 dla żywności), co wynika z jednoczesnego, silnego wzrostu wszystkich badanych zmiennych w badanym czasie.

## 💡 Wnioski z analizy
* Zaobserwowano silną korelację dodatnią między wzrostem cen a otyłością – odsetek otyłości wzrósł w tym czasie o blisko 69,7%.
* Fakt, że społeczeństwo tyje pomimo rosnących cen nominalnych, sugeruje stosunkowo niską elastyczność cenową popytu na żywność. Konsumenci w odpowiedzi na inflację nie redukują spożycia kalorii, lecz najpewniej kierują się w stronę tańszych, bardziej przetworzonych produktów.
* Z analizy wynika, że koszty usług i pracy rosną szybciej niż ceny pożywienia. To sprawia, że w ujęciu relatywnym kalorie wciąż pozostają bardzo łatwo dostępnym dobrem.
* **Ostateczna konkluzja:** Polacy tyją, a ceny rosną, jednak statystyka udowadnia, że "Polacy tyją wolniej niż rosną ceny".
