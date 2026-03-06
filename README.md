# dict_kk_myspell

Kazakh (Kazakhstan) word list for the [ABCx3](https://abcx3.com) crossword game.

## Source

Word list derived from **[myspell-kk](https://github.com/kergalym/myspell-kk)** — a Kazakh dictionary for Hunspell developed under the OpenOffice Lingucomponent project. The base word data originates from the aspell-kk\_KZ package (v0.60, by Alexey Lipchansky), with affix rules for Kazakh morphology developed by Kaldybai Bektaiuly.

## Processing

The raw Hunspell files (`kk_KZ.dic` + `kk_KZ.aff`, ~54,000 stems) were processed for game use by `expand_hunspell_kk.py`:

- Parsed all Hunspell affix rules (51 suffix flag rules covering Kazakh noun case declension, possessive suffixes, verb conjugation, etc.)
- Expanded all stems into their full inflected forms
- **Removed all 395 proper nouns** (Kazakh personal names — detected by initial uppercase letter)
- Filtered out abbreviations (all-caps entries)
- Removed compound words with hyphens or spaces
- Required at least one Kazakh vowel per word (а е і о у ы ә ө ұ ү)
- Kept only words consisting entirely of Kazakh Cyrillic characters

**Final result: 1,157,405 unique inflected word forms** stored in `words_kk-KZ.txt`.

## Kazakh Alphabet

The word list uses the standard Kazakh Cyrillic script (42 letters, as officially used in Kazakhstan). Unique Kazakh letters not found in Russian: **ә і ң ғ ү ұ қ ө һ**.

Alphabetical order used in the game: `аәбвгғдежзийкқлмнңоөпрстуұүфхһцчшщъыіьэюя`

No character mappings are needed — each Kazakh letter represents a phonemically distinct sound and has its own tile.

## Regeneration

To regenerate the word list from source:

1. Download the source Hunspell files from [myspell-kk](https://github.com/kergalym/myspell-kk):
   ```
   wget https://raw.githubusercontent.com/kergalym/myspell-kk/master/kk_KZ.aff
   wget https://raw.githubusercontent.com/kergalym/myspell-kk/master/kk_KZ.dic
   ```

2. Run the expansion script:
   ```
   python3 expand_hunspell_kk.py
   ```

## License

The derived word list is licensed under the **[Mozilla Public License 1.1 (MPL 1.1)](https://www.mozilla.org/en-US/MPL/1.1/)**, chosen from the triple-license (GPL 2.0+ / LGPL 2.1+ / MPL 1.1) offered by the myspell-kk source.

The expansion script (`expand_hunspell_kk.py`) is licensed under MIT.

Attribution:
- **myspell-kk** by Kaldybai Bektaiuly and contributors — https://github.com/kergalym/myspell-kk
- **aspell-kk** (original word data) by Alexey Lipchansky

## Usage

This word list is used as the Kazakh (Kazakhstan) dictionary in the ABCx3 game backend.
