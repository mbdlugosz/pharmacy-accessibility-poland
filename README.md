# Dostępność Aptek w Polsce

Analiza dostępności aptek w Polsce na poziomie województw z uwzględnieniem dwóch perspektyw:

- liczby aptek na 100 tys. mieszkańców ogółem,
- liczby aptek na 100 tys. mieszkańców w wieku 70+.

Projekt ma charakter eksploracyjny i pokazuje, czy rozmieszczenie aptek lepiej odpowiada całkowitej liczbie ludności, czy także strukturze wieku mieszkańców.

## Cel projektu

Celem analizy jest porównanie dostępności aptek pomiędzy województwami oraz sprawdzenie, czy regiony o większym udziale seniorów mają proporcjonalnie lepszy dostęp do infrastruktury farmaceutycznej.

Główne pytania badawcze:

- Jak bardzo różni się liczba aptek w przeliczeniu na 100 tys. mieszkańców między województwami?
- Czy obraz zmienia się po ograniczeniu populacji odniesienia do grupy 70+?
- Które województwa wypadają najlepiej i najsłabiej w obu ujęciach?

## Zakres analizy

Analiza została wykonana w notebooku [EDA.ipynb](EDA.ipynb).

Workflow obejmuje:

1. wczytanie rejestru aptek,
2. odfiltrowanie aktywnych placówek,
3. agregację liczby aptek do poziomu województw,
4. połączenie danych z informacją o liczbie mieszkańców i seniorów 70+,
5. wyliczenie wskaźników na 100 tys. mieszkańców,
6. wizualizację wyników na wykresach i mapie Polski.

## Źródła danych

Repozytorium zawiera lokalne pliki wejściowe w katalogu `data/`:

- `data/Rejestr_Aptek_stan_na_dzien_2026-04-21.csv` - rejestr aptek,
- `data/LUDN_2137_CTAB_20260414235116.csv` - dane o ludności ogółem i populacji 70+,
- `data/wojewodztwa/` - granice województw wykorzystywane do wizualizacji przestrzennej.

## Metodologia

W analizie:

- uwzględniono aktywne apteki i punkty apteczne,
- ujednolicono nazwy województw, aby możliwe było połączenie zbiorów,
- policzono dwa wskaźniki:
  - `apteki_na_100k` - liczba aptek na 100 000 mieszkańców,
  - `apteki_na_100k_70plus` - liczba aptek na 100 000 mieszkańców w wieku 70+,
- porównano województwa w rankingu oraz na mapie.

## Najważniejsze wnioski

Na podstawie wyników zapisanych w notebooku:

- zróżnicowanie dostępności aptek względem całej populacji jest relatywnie umiarkowane między województwami,
- po przeliczeniu wskaźnika na populację 70+ różnice wyraźnie rosną,
- sugeruje to, że rozmieszczenie aptek jest lepiej dopasowane do ogólnej liczby mieszkańców niż do struktury wieku,
- najwyższy wskaźnik dostępności dla seniorów 70+ odnotowano w województwie wielkopolskim: `283` apteki na 100 tys. osób 70+,
- najniższy wskaźnik dla seniorów 70+ odnotowano w województwie śląskim: `206` aptek na 100 tys. osób 70+.

Przykładowe wyniki z notebooka:

- najwyższe wartości `apteki_na_100k`: `LUBELSKIE`, `WIELKOPOLSKIE`, `ŁÓDZKIE`,
- najwyższe wartości `apteki_na_100k_70plus`: `WIELKOPOLSKIE`, `PODLASKIE`, `PODKARPACKIE`,
- najniższe wartości `apteki_na_100k_70plus`: `ŚLĄSKIE`, `ŚWIĘTOKRZYSKIE`, `DOLNOŚLĄSKIE`.

## Technologie

Projekt został przygotowany w Pythonie z użyciem:

- `pandas`
- `geopandas`
- `matplotlib`
- `seaborn`
- `adjustText`
- `jupyterlab`

Zależności są zdefiniowane w [pyproject.toml](pyproject.toml) oraz zablokowane w `uv.lock`.

## Struktura repozytorium

```text
pharmacy-accessibility-poland/
|-- data/
|   |-- Rejestr_Aptek_stan_na_dzien_2026-04-21.csv
|   |-- LUDN_2137_CTAB_20260414235116.csv
|   `-- wojewodztwa/
|-- EDA.ipynb
|-- pyproject.toml
`-- uv.lock
```

## Jak uruchomić projekt

### Wariant z `uv`

```bash
uv sync
uv run jupyter lab
```

Następnie otwórz notebook `EDA.ipynb`.

### Wariant z `pip`

```bash
python -m venv .venv
.venv\Scripts\activate
pip install -e .
jupyter lab
```

## Potencjalne rozszerzenia

- analiza na niższym poziomie agregacji, np. powiatów lub gmin,
- uwzględnienie gęstości zaludnienia i urbanizacji,
- analiza zmian w czasie dla kolejnych okresów,
- rozszerzenie o wskaźniki odległości lub czasu dojazdu do najbliższej apteki.

## Autor

Projekt został przygotowany jako portfolio / projekt analityczny dotyczący dostępności usług farmaceutycznych w Polsce.
