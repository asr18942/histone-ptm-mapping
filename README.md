# Histone PTM Map

A single-page tool for making bottom-up histone figures:

- **Coverage map** – the sequence split into blocks of 5, each detected peptide/proteoform underlined, and PTM icons drawn on its line at the modified residue.
- **Proteoform matrix** – one row per proteoform, one column per modified site, coloured dots for each mark (black = unmodified), with a schematic header.

Everything runs in the browser. Nothing is uploaded; your inputs are saved only in your own browser.

## Use it

Open the GitHub Pages site for this repository, or download `index.html` and open it in any browser.

## Input syntax

**Sequence** – paste plain or FASTA text, or pick a preset (human H3.1, H3.3, H4, H2A, H2B; initiator Met removed, so H3 K4 = residue 4). If your sequence starts with M, set *First residue #* to 0.
> Check preset sequences against UniProt before publishing.

**Detected peptides** – one proteoform per line; each line gets its own underline and matrix row.

| Write | Meaning |
|---|---|
| `TKQTAR` | unmodified peptide |
| `TK[me3]QTAR` | K4me3 |
| `K[ac]STGGK[ac]APR` | K9ac + K14ac on one peptide |
| `K[+42.011]STGGKAPR` | mass shift (matched to the closest known mark) |
| `[ac]-SGRGKGGK` | protein N-terminal acetylation |
| `…KGK-[am]` | C-terminal mark |
| `KSTGGKAPR @9` | force the start position |
| `9-17` | a residue range with no sequence check |
| `# note` | ignored |

**Extra modification sites** – marks not tied to a peptide. Commas separate entries; spaces (or `/`, `&`, `+`) combine marks into one combinatorial proteoform.

```
K27me3, K36me2, Ntac K5ac K8ac, K8ac M54ox
```

`Nt…` / `Ct…` refer to the protein termini (e.g. `Ntac`, `Nt-ac`).

**Mark names** – `me1 me2 me3 ac ph ox (O) ub cr pr bu su la hib cit`, full names (`acetyl`, `trimethyl`, …) or any custom label.

## Exporting

- **Copy SVG** – paste straight into Illustrator, Inkscape or PowerPoint.
- **Download SVG / PNG** – PNG at 2–6× (3× ≈ 300 dpi).

## Tips

- Drag across residues in the coverage map to add a peptide; click a residue to add or remove a mark.
- The figure uses system fonts (Arial, Helvetica, Courier New, Times New Roman, Calibri) so exports match what you see.
