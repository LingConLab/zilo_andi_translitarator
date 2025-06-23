## Zilo Andi Transliterator

This is an FST converter that converts modified Avar Cyrillic alphabet (used in Zilo Andi, zilo1238) to IPA and vice versa. It includes the following additions:

- <ӏ> (U+04CF, [Cyrillic small letter Palochka](https://en.wikipedia.org/wiki/Palochka)) and <Ӏ> (U+04C0, [Cyrillic letter Palochka](https://en.wikipedia.org/wiki/Palochka)) can be used interchangeably.  It's also possible to use <I> (U+0049, Latin Capital letter I) and <1> (U+0031, Digit One) for the same purpose.
- Nasalisation is absent in Avar, so to denote nasalisation in Zilo Andi Cyrillic, several options are possible: <ᴴ> (U+1D34, Modifier Letter Capital H, e.g., <аᴴ>), <2> (U+0031, Digit Two, e.g., <а2>), or a tilde over the vowel (e.g., <а̃>).
- We expect [je] following a vowel or in word-initial position to be spelled as <йе>, which contradicts Russian spelling.
- The sequence <лъ> is ambiguous. We decided to use <лъ> to denote a lateral fricative [ɬ], so be carefull for other contexts when it is actually [lʔ].

Please refer to the transliterator as follows:

```
Moroz G. (2025) An FST translitarator from Zilo Andi Cyrillic to IPA, https://github.com/LingConLab/zilo_andi_translitarator
```

## Usage

```
$ make
$ echo "гьарзалъир" | hfst-proc andi_zilo_cyrillic2ipa.hfstol

^гьарзалъир/harzalʔir/harzaɬir$ 
```

Make sure you have `hfst` and `lexd` installed. Here are the instructions.

```
$ curl -s https://apertium.projectjj.com/apt/install-nightly.sh | sudo bash
$ sudo apt-get install hfst lexd
```

All metadata could be seen using the following command:

```
$ hfst-edit-metadata zilo_andi_cyrillic2ipa.hfstol
```

I decided not to do the reverse IPA to cyrillic side as a simple reverse after I gathered all possible capitals:

```
$ echo "anʒilo" | hfst-proc andi_zilo_ipa2cyrillic.hfstol 

^anʒilo/АНЖИЛО/АНЖИЛо/АНЖИлО/АНЖИло/АНЖиЛО/АНЖиЛо/АНЖилО/АНЖило/АНжИЛО/АНжИЛо/АНжИлО/АНжИло/АНжиЛО/АНжиЛо/АНжилО/АНжило/АнЖИЛО/АнЖИЛо/АнЖИлО/АнЖИло/АнЖиЛО/АнЖиЛо/АнЖилО/АнЖило/АнжИЛО/АнжИЛо/АнжИлО/АнжИло/АнжиЛО/АнжиЛо/АнжилО/Анжило/аНЖИЛО/аНЖИЛо/аНЖИлО/аНЖИло/аНЖиЛО/аНЖиЛо/аНЖилО/аНЖило/аНжИЛО/аНжИЛо/аНжИлО/аНжИло/аНжиЛО/аНжиЛо/аНжилО/аНжило/анЖИЛО/анЖИЛо/анЖИлО/анЖИло/анЖиЛО/анЖиЛо/анЖилО/анЖило/анжИЛО/анжИЛо/анжИлО/анжИло/анжиЛО/анжиЛо/анжилО/анжило$
```
