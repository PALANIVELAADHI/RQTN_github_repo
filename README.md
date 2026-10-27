# Ramanujan-expanded quantum Tanner codes for quantum networks: finite-size benchmark

Code, data, figures and manuscript for *"Ramanujan-Expanded Quantum Tanner Codes for Reliable Quantum Networks: Finite-Size Distance, Decoding, and Logical Error-Rate Analysis"*.
## By Dr.R.Palanivel
## Layout
- `qtanner/` – library: PSL(2,q) / PGL(2,q) groups, local codes, quantum Tanner code on the left-right Cayley complex (double cover and bipartite variants), GF(2) tools, Cayley spectra.
- `study/` – the scripts that produce every number in the paper:
  `s1_params.py` (parameters, spectra), `s2_ler.py` (Monte Carlo: greedy, BP+OSD-0, MWPM), `s3_network.py` (loss, latency, throughput, cost), `s4_figures.py` (all figures).
- `data/` – raw JSON results (`params.json`, `ler.json`, `network.json`) and earlier integer-programming results (`prior_*.json`).
- `figures/` – all figures used in the paper.

- `tests/` – unit tests (group axioms, CSS commutation, bipartite variant).

## Reproduce
```bash
pip install -r requirements.txt
python -m pytest -q tests
cd study && python3 s1_params.py && python3 s2_ler.py && python3 s3_network.py && python3 s4_figures.py
cd ../paper && python3 make_paper.py && pdflatex main && bibtex main && pdflatex main && pdflatex main
python3 make_docx.py      # Word version (needs pandoc, python-docx)
```
`s2_ler.py` takes about 15-20 minutes on one core. All random draws use fixed seeds.

## Publish on GitHub
```bash
git init && git add . && git commit -m "Ramanujan quantum Tanner network benchmark"
git branch -M main
git remote add origin https://github.com/<YOUR-USERNAME>/ramanujan-quantum-tanner-network.git
git push -u origin main
```

## License
Code: MIT (`LICENSE`). Data, figures and paper text: CC BY 4.0.
