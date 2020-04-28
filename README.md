# DyadRatiosFix
Stimson dyad-ratios code with bug fixes.

This is a slightly improved version of the R code for Jim Stimson's dyad-ratios calculator which is currently listed on his website: http://stimson.web.unc.edu/software/.

This code is able to replicate the WCalc (Windows VB.NET) and MCalc (C++) versions of the calculator, which can be used to aggregate and harmonise survey measurements asking different questions on the same topic over time. Please see Professor Stimson's website for full explanation and documentation. 

The bug fixes are as follows:

- Line 128: Forcing curate to quarterly format for unit=Q which stops, means we do not generate fake dates for the quarter placeholders (e.g. 5/29/2010 would not become 2/29/2010 in curdate) and thus collapse the algorithm.
- Line 148, 159 & 173: Making findper search for periods in the original date records when deciding if an entry is in range, not the curdate changed ones, means that we will not miss entries with a date after April (which in curdate terms would be past the end of the period).
- Small as.character fix on line 170 which just stops things falling over based on whether individual systems/users read strings as characters.
- Line 182-186: Adding code to make sure the final record in a series is included (and if necessary  aggregated) in the issue matrix when it is found, instead of R stopping at that line having identified it as the final row (as it currently does in Extract v5).

With these fixes, the R code replicates with MCalc and WCalc outputs to within 0.0001% on annual and quarterly estimations.
