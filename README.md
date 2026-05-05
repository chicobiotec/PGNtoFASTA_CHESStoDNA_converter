# ♟️ PGNtoFASTA - Chess to DNA Converter

An experimental tool that converts chess games into DNA sequences.

## Concept

Each square on the chessboard (64 total) is mapped to a codon (64 possible combinations of A, C, G, T).

Thus:

* move = origin → destination
* each move generates **2 codons**
* a game becomes a **DNA sequence**

Internal pipeline:

```
PGN → UCI → DNA → FASTA
```

---

## Features

* Support for **multiple games (multi-PGN)**
* **Multi-FASTA** generation
* Export of **metadata in TSV format**
* Optional limit on number of moves
* Visualization of board → codon mapping
* Robust parsing via chess.js

---

## Encoding

Each move:

```
from → to = 2 codons = 6 nucleotides
```

Example:

```
e2e4 → (codon_e2)(codon_e4)
```

---

## Promotions

Promotions are encoded using an impossible repetition pattern:

```
destination → destination (repeated)
```

Table:

| Piece  | Repetitions |
| ------ | ----------- |
| Knight | 1           |
| Bishop | 2           |
| Rook   | 3           |
| Queen  | 4           |

This preserves unambiguous decoding.

---

## Outputs

### 1. FASTA

```
>cDNA_0001|moves=20|nt=120
ACGT...
```

### 2. Metadata (TSV)

Includes:

* players
* event
* number of moves
* sequence length
* promotions

---

## Applications

* Phylogenetic analysis of chess games
* Opening clustering
* Player style analysis
* Game sonification
* Artificial bioinformatics experiments

---

## Usage

1. Open the HTML file in a browser
2. Paste a PGN
3. Click **Convert**

---

## Notes

* Requires `chess.js` (CDN included)
* May fail offline depending on browser
* Very large files may be slow

---

## Tests

Includes internal tests for:

* mapping consistency
* PGN parsing
* FASTA generation

---

## License

Free for experimental and academic use.

---

## Third Party Licenses 

This project uses the Chess.js library, which is licensed under the BSD 2-Clause License.
Chess.js: Copyright (c) Jeff Hlywa
Source: https://github.com/jhlywa/chess.js
The full license text for Chess.js is included in the LICENSE file of this project.

## Disclaimer

This software is provided "as is", without warranty of any kind. See the LICENSE file for details.
