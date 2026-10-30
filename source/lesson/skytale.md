# Skitala

Skitala (engl. skytale) je jedan od najstarijih poznatih alata za šifrovanje, koji potiče iz stare Grčke oko 400. godine pre nove ere. Bila je to jednostavna cilindrična naprava koju su Spartanci koristili da šalju tajne poruke tokom vojnog pohoda.

Traka od pergamenta ili kože namotavala se oko drvene šipke (*skytale*) određenog prečnika. Poruka se zatim pisala uzdužno duž namotane trake. Da bi dešifrovao, primalac je ponovo namotavao traku oko šipke istog prečnika i čitao poruku uzdužno, na isti način kao što je i napisao.

Ako želiš da šifruješ poruku:

```text
attackatdawn
```

i izabereš šipku koja omogućava **3 slova po obrtaju**, traka ide oko nje 4 puta. Pišeš poruku duž šipke, red po red, 4 slova po redu (po jedno na svakom obrtaju), formirajući tabelu:

```text
a t t a
c k a t
d a w n
```

Šifrovani tekst se zatim dobija čitanjem kolona po kolone (ovaj je redosled slova na odmotanoj traci):

```text
acdtkatawatn
```

Da bi dešifrovao poruku, primalac ponovo namotava traku oko šipke istog prečnika i čita red po red da bi rekonstruisao originalnu poruku.

## Prvi zadatak

Napravi konzolnu aplikaciju u bilo kom programskom jeziku da šifruješ i dešifruješ poruke koristeći Skitalu.

Dozvoljena azbuka za poruke sadrži samo mala slova engleske abecede:

```text
Σ = { a, b, c, d, e, f, g, h, i, j, k, l, m, n, o, p, q, r, s, t, u, v, w, x, y, z }
```

Razmaci, velika slova, brojevi i drugi znakovi nisu dozvoljeni!

U prvoj liniji ulaza nalazi se poruka `m` dužine najviše sto karaktera. U drugoj liniji se nalazi ceo broj `k` (broj kolona u tabeli za šifrovanje). U trećoj liniji se nalazi ceo broj `s` (1 za šifrovanje, 2 za dešifrovanje).

### Test primer 1

Ako je ulaz:

```text
attackatdawn
4
1
```

izlaz treba da bude:

```text
acdtkatawatn
```

### Test primer 2

Ako je ulaz:

```text
acdtkatawatn
4
2
```

izlaz treba da bude:

```text
attackatdawn
```

## Saveti za rešavanje

Za **šifrovanje**, napiši otvoreni tekst red po red u tabelu sa `k` kolona. Čitaj tabelu kolona po kolona da dobiješ šifrat.

Za **dešifrovanje**, napiši šifrat kolona po kolona u tabelu sa `k` kolona (svaka kolona sadrži dužinu poruke podeljenu sa `k` slova), pa čitaj tabelu red po red da rekonstrušeš otvoreni tekst.

## Složeniiji zadaci sa Skitalom (opciono)

### Proširi dozvoljenu azbuku

Uključi velika slova, razmake, brojeve i znakove interpunkcije.

### Koristi funkcije

Napravi funkcije `encrypt()` i `decrypt()` da bi kod bio modularan.

### Napravi klasu

Implementiraj klasu `SkytaleCipher` koja čuva `k` i pruža metode za šifrovanje i dešifrovanje.

### Šifruj i dešifruj fajlove

Izmeni program tako da čita otvoreni ili šifrovani tekst iz fajla i rezultat upisuje u drugi fajl.

### Obradi nepotpune redove

Izmeni program tako da, ako je poslednji red kraći od `k`, i dalje ispravno šifruje i dešifruje, obrađujući nedostajuća polja na odgovarajući način.
