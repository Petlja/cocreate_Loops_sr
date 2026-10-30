# Cezarova šifra

Jedan od velikih vojskovođa koji je koristio šifrovane poruke bio je Julije Cezar, oko 50. godine pre nove ere. Koristio je jednostavnu šifru poznatu kao Cezarova šifra da zaštiti vojne komunikacije. Ova šifra pomera svako slovo za određeni broj mesta u abecedi.

Na primer, ako napišeš `NIKOLATESLA` i pomeriš svako slovo tri mesta ulevo:

```text
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
X Y Z A B C D E F G H I J K L M N O P Q R S T U V W
```

Slovo `N` postaje `K`, `I` postaje `F` i tako dalje. Dakle, svako slovo se zamenjuje drugim slovom koje je na određenoj udaljenosti u abecedi.

**Dešifrovanje** radi isto, ali obrnuto. Da bi dešifrovao šifrat, pomeri svako slovo nazad tri mesta udesno:

```text
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
D E F G H I J K L M N O P Q R S T U V W X Y Z A B C
```

Slovo `K` postaje `N`, `F` postaje `I` i tako dalje. Rezultat ovog pomeranja je originalna dešifrovana poruka `NIKOLATESLA`.

![Caesar Cipher Left Shift](./images/caesar1.png)

## Zadatak za razmišljanje

Razmisli kako bi napravio konzolnu aplikaciju u bilo kom programskom jeziku koja će šifrovati i dešifrovati poruke koristeći Cezarovu šifru.

```{infonote}
Prvi učenik (*vozač*) treba da se fokusira na sintaksu dok piše kod za šifrovanje poruke. Drugi učenik (*navigator*) treba da prati kod, predlaže poboljšanja i postavlja pitanja. Nakon šifrovanja, zamenite uloge da biste dešifrovali.
```

Dozvoljena azbuka za poruke (i za otvoreni i za šifrovani tekst) može da sadrži samo mala slova engleske abecede:

```text
Σ = { a, b, c, d, e, f, g, h, i, j, k, l, m, n, o, p, q, r, s, t, u, v, w, x, y, z }
```

Razmaci, velika slova, brojevi i drugi znakovi nisu dozvoljeni.

U prvoj liniji ulaza nalazi se poruka `m` dužine najviše sto karaktera, u drugoj liniji ceo broj `n` koji predstavlja vrednost pomeraja (1–25), a u trećoj liniji ceo broj `s` koji predstavlja smer šifrovanja. Ako je `s=1`, poruka treba da bude šifrovana, a ako je `s=2`, treba da bude dešifrovana.

### Test primer 1

Ako je ulaz:

```text
nikolatesla
3
1
```

izlaz treba da bude:

```text
kfhlixqbpix
```

### Test primer 2

Ako je ulaz:

```text
kfhlixqbpix
3
2
```

izlaz treba da bude:

```text
nikolatesla
```

## Saveti za rešavanje

Pošto engleska abeceda ima 26 slova, pozicija svakog slova može se predstaviti brojem od 0 do 25.

* a → 0
* b → 1
* c → 2
* ...
* z → 25

Da bi se **šifrovalo** slovo, možeš koristiti sledeću formulu:

```text
new_letter_position = (current_letter_position - shift_value + 26) mod 26
```

`current_letter_position` predstavlja numeričku vrednost slova u azbuci, `shift_value` predstavlja broj pozicija za pomeraj (1–25), `+ 26` obezbeđuje da vrednost ne postane negativna, a `mod 26` obezbeđuje da se vrati na početak abecede.

Da bi se **dešifrovalo** slovo, možeš koristiti sledeću formulu:

```text
new_letter_position = (current_letter_position + shift_value) mod 26
```

Slično kao kod šifrovanja, ali se vrednost pomeraja sabira, pa vrednost ne može da postane negativna i `+ 26` nije potreban.

## Složeniiji zadaci sa Cezarovom šifrom (opciono)

### Proširi dozvoljenu azbuku

Napravi konzolnu aplikaciju u bilo kom programskom jeziku koja će šifrovati i dešifrovati poruke koristeći Cezarovu šifru, ali sa proširenom azbukom.

Aplikacija treba da šifruje ili dešifruje samo mala i velika slova. Razmaci, brojevi i znakovi interpunkcije treba da ostanu nepromenjeni.

U prvoj liniji ulaza nalazi se poruka `m` dužine najviše sto karaktera, u drugoj liniji ceo broj `n` (vrednost pomeraja od 1 do 25), a u trećoj liniji ceo broj `s` (1 za šifrovanje, 2 za dešifrovanje).

## Koristi funkcije

Napravi dve funkcije: jednu za šifrovanje poruka i jednu za dešifrovanje poruka. Koristi napravljene funkcije u glavnom programu.

Ovde možete raditi u paru — jedna osoba treba da šifruje poruku, a druga da je dešifruje!

## Napravi klasu

Napravi klasu `CaesarCipher` koja sadrži:

- konstruktor sa parametrom koji prihvata vrednost pomeraja i obezbeđuje da je vrednost u dozvoljenom opsegu (0–25),
- privatno svojstvo za čuvanje vrednosti pomeraja, sa getter i setter metodama,
- javnu metodu za šifrovanje poruke,
- javnu metodu za dešifrovanje poruke i
- opciono, privatnu metodu za obradu poruka koju koriste obe metode.

Koristi napravljenu klasu u glavnom programu.

## Prihvati argumente komandne linije

Umesto čekanja na unos korisnika, napravi konzolnu aplikaciju koja prihvata sledeće argumente komandne linije:

1. argument `m` za poruku,
2. argument `n` za vrednost pomeraja (`0` do `25`), i
3. argument `s` za smer šifrovanja (`1` za šifrovanje, `2` za dešifrovanje).

## Šifruj i dešifruj fajlove

Iskoristi dosadašnje znanje da napraviš konzolnu aplikaciju za šifrovanje i dešifrovanje tekstualnih fajlova koristeći Cezarovu šifru.

Aplikacija treba da prihvata sledeće argumente komandne linije:

1. argument `m` za ime fajla (ili putanju),
2. argument `n` za vrednost pomeraja (`0` do `25`), i
3. argument `s` za smer šifrovanja (`1` za šifrovanje, `2` za dešifrovanje).
