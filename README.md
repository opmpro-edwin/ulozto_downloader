# Ulož.to downloader

Paralelní stahovač z [Ulož.to](http://ulozto.cz) inspirovaný [Vžum](http://vzum.8u.cz/) (credits to Popcorn).

Narozdíl od originálního Vžum je tato verze napsaná v Pythonu, dá se provozovat jednoduše i na Linuxu a zdrojový kód je veřejně dostupný, což umožňuje další forky a rozšíření do budoucna. Například by mohla vzniknout "serverová" verze s webovým rozhraním.

**Nápady na další vylepšení (případně rovnou pull requesty) vítány :-)**

#### Disclaimer

Také existuje [jiná velmi podobná Pythoní verze](https://github.com/yaqwsx/utility/blob/master/vzum/vzum) vyvinutá Honzou Mrázkem. Dozvěděl jsem se o ní samozřejmě až po dopsání mojí verze při pátrání, kam bych mohl svoji verzi zveřejnit (vtipné je to, že na některé věci jsme zvolili velmi podobné postupy aneb konvergentní evoluce není kec :-D).

## Klíčové vlastnosti

* Sám pozná downloady, kde Ulož.to umožňuje stahovat bez CAPTCHA kódů
* Automaticky opisuje CAPTCHA kódy, pokud jsou splněny všechny nároky a je zvolen parametr --captcha a

  **Tensorflow instalovaný pomocí Pipu vyžaduje AVX instrukce (Intel Sandy Bridge a novější)**
* V ostatních případech na začátku postupně vyptá od uživatele opsání CAPTCHA kódů
* Umí navazovat přerušená stahování (pokud se zachová stejný počet částí)
* Konzolový status panel

## Použití

```shell
./ulozto_downloader.py --parts 15 --captcha m 'https://ulozto.cz/file/TKvQVDFBEhtL/debian-9-6-0-amd64-netinst-iso'
```

## Requirements

* Python 3
* Nějaké knihovny pro Python 3:
  * Tkinter (balík `python3-tk` na Debianu)
  * Pillow s ImageTK (balík `python3-pil.imagetk` na Debianu)
* Pro funkční automatické opisování:
  * Tensorflow
  * Numpy
  * [Vytrénovaný model](https://github.com/JanPalasek/ulozto-captcha-breaker/releases) ve stejné složce jako ulozto_downloader.py
