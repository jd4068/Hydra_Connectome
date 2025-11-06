Hydra GPCR–Neuropeptide discovery & cell–cell connectivity analysis pipeline

Pipeline and code to identify class A GPCRs and neuropeptide precursors in Hydra vulgaris, predict receptor–peptide binding using AlphaFold-Multimer + membrane-topology heuristics, and build peptide–receptor cell–cell connectivity matrices from scRNA-seq.

Key steps implemented

1. HMM search for class A GPCRs (PF00001 → HMMER). Code for this can be found under src/hmmer 

2. TM-filtering with Phobius (keep sequences with 4–9 TM helices). (this was done using the online platform https://phobius.sbc.su.se/index.html and then filtering) 

3. Sequence clustering & phylogeny visualization using CLANS (all-vs-all BLAST). This was done using the online paltform to make the alignment and then using the GUI from the downloaded version to make a figure (https://toolkit.tuebingen.mpg.de/tools/clans). settings used are found in the methods and the final CLANS made can be dowloaded from /data and opened within CLANS 

4. Secretome and neuropeptide precursor detection ( motif/cleavage-pattern search SignalP +) code for the motif/cleavage pattern search is found under src/patternsearch

5. Receptor–peptide ranking with AlphaFold-Multimer ipTM score combined with DeepTMHMM-derived topology heuristics.

6. Cell–cell connectivity matrix construction from scRNA-seq: multiply receptor expression (receiver cell) × peptide expression (sender cell) × AF-binding-score; aggregate by peptide–receptor and collapse to cell-type level.

7. Network analyses: hub detection, clustering, rich-club analysis (subsampling to ~250 neurons to simulate realistic Hydra size).
