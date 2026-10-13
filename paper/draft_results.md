# Results draft

> DRAFT generated from the result files. Verify every number, rewrite in your own words, and do not keep claims the data do not support.

## Data
The public collection contained 84,484 scans. After cleaning (removed: 7,341 exact duplicate (one copy kept), 466 same image under different class folders), 76,677 scans from 4,656 patients remained. Patients that shared an image or had near-identical scans were linked into groups, and groups were split into training (61,154), validation (7,789) and test (7,734) scans, stratified by class. No patient group and no byte-identical image appears in more than one split.

## Main results
- CNN + softmax (baseline): accuracy 93.69% (95% CI 93.17-94.19), macro-F1 0.9207, ECE 0.0511, error-detection AUROC 0.831, 488 errors on 7,734 test scans (seed 42).

## Comparison with the baseline
(paired tests not available - run notebook 04)

## Uncertainty
- CNN + softmax (baseline): mean uncertainty 0.007 on correct vs 0.087 on wrong predictions; accuracy on the 90% / 80% most certain scans 96.98% / 97.88%.

## External validation
External scans: 24,000 files; 11,903 (49.6%) were removed because they overlap with the training data (file or image hash); 97 known-class and 12,000 unseen-class scans were evaluated.
- CNN + softmax (baseline): external accuracy 58.76% (95% CI 50.52-69.07) vs 93.69% internal (-34.93 pp), macro-F1 0.5209.
- CNN + softmax (baseline): unseen-disease detection AUROC 0.314 (own score), 0.314 (1 - max probability), 0.316 (entropy).

## Limitations (auto-detected, expand as needed)
- Fewer than 3 seeds for some variants ({'cnn_softmax': 1}); report mean +/- std over >= 3 seeds before claiming differences.
- The external dataset overlaps substantially with the training data; it is only partly independent.
- Labels in public OCT collections are not expert-verified for every scan; some label noise is expected (see dropped.csv for conflicts that were removed).
- Grad-CAM maps are saliency maps, not validated lesion segmentations.
