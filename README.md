# Algoritmi

Zbirka implementacija algoritama i struktura podataka u C++-u.

## Sadržaj

| Mapa | Opis |
|------|------|
| [`bloom/`](bloom/) | Bloom filter – probabilistička struktura za provjeru pripadnosti elementa skupu |
| [`ford-fulkerson/`](ford-fulkerson/) | Ford-Fulkersonov algoritam za maksimalni protok u mreži |
| [`particioniranje-multiskupa-brojeva/`](particioniranje-multiskupa-brojeva/) | Generiranje svih particija multiskupa brojeva |
| [`quad-tree/`](quad-tree/) | Quad stablo (QuadStablo) za pohranu točaka u 2D prostoru |

## Bloom filter

Generički predložak `BloomFilter<elementtype, velicina_polja>` (zadana veličina polja je `BLOOM = 1000` bitova). Koristi tri funkcije sažimanja izvedene iz `std::hash`, a stanje filtra sprema u datoteku `bloom.txt`.

Interaktivni izbornik nudi:
1. stvaranje (resetiranje) Bloom filtra,
2. dodavanje vrijednosti,
3. provjeru vrijednosti (odgovor „možda je u filtru” ili „nije u filtru”),
4. izlazak iz programa.

Datoteke:
- `bloom.h`, `bloom.cpp` – implementacija i glavni program
- `bloom_komentari.h`, `bloom_komentari.cpp` – ista implementacija s detaljnim komentarima
- `Izracun_bloom_filter.xlsx` – izračun parametara Bloom filtra (vjerojatnost lažno pozitivnih rezultata)

## Ford-Fulkerson

Računa maksimalni protok između izvora i slijeva u grafu prikazanom matricom susjedstva, pri čemu se putevi povećanja traže pretraživanjem u dubinu (DFS). Primjer u `main()` koristi graf sa 6 vrhova, izvor `0` i slijev `3`.

## Particioniranje multiskupa brojeva

Rekurzivno (backtrackingom) ispisuje sve particije zadanog multiskupa. Svaki element se ili stavlja u novi blok ili dodaje u neki od postojećih blokova. Primjer koristi multiskup `{1, 4, 9, 9, 10}`.

## Quad stablo

Struktura `QuadStablo` dijeli pravokutni prostor zadane širine i visine na četiri kvadranta (SZ, SI, JZ, JI). Interaktivni izbornik omogućuje:
1. unos točke,
2. provjeru postoji li točka u stablu,
3. uklanjanje točke,
4. izlaz.

## Prevođenje i pokretanje

Potreban je C++ prevoditelj s podrškom za C++11 ili noviji (npr. `g++`).

```bash
# Bloom filter
g++ -std=c++17 bloom/bloom.cpp -o bloom_filter && ./bloom_filter

# Ford-Fulkerson
g++ -std=c++17 ford-fulkerson/ford_fulkerson.cpp -o ford_fulkerson && ./ford_fulkerson

# Particioniranje multiskupa
g++ -std=c++17 particioniranje-multiskupa-brojeva/part.cpp -o part && ./part

# Quad stablo
g++ -std=c++17 quad-tree/quadstablo.cpp -o quadstablo && ./quadstablo
```

> Napomena: Bloom filter stvara datoteku `bloom.txt` u trenutnom radnom direktoriju. Prije dodavanja ili provjere vrijednosti potrebno je odabrati opciju 1 kako bi se datoteka stvorila.
