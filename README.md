## Problem Description :
Given an equal number of men and women to be paired for marriage, each man ranks all the women in order of his preference and each women ranks all the men in order of her preference.

A stable set of engagements for marriage is one where no man prefers a women over the one he is engaged to, where that other woman also prefers that man over the one she is engaged to. I.e. with consulting marriages, there would be no reason for the engagements between the people to change.

Gale and Shapley proved that there is a stable set of engagements for any set of preferences and the first link above gives their algorithm for finding a set of stable engagements.

## Problem Tackling :
Men’s behavior:

1. make proposals according to the ordering
(ignoring the existing pairs)

2. never leave the current partner on their
own

3. never repeat a rejected proposal

4. keep in memory: position in the list  current
partner

Women’s behavior:

1. accept a proposal if no partner.

2. or an improvement over current partner

3. keep in memory: current partner

## PseudoCode : 
While there exists an unmarried man:

1. Pick an arbitrary unmarried man M

2. Choose the top woman W from his list to whom he hasn't proposed yet

3. If W is free or prefers M over her current husband, then marry M and W

## Additional Info:
We'll write a Python function stableMatching(n, menPreferences, womenPreferences) that gets the number n of women and men, preferences of all women and men, and outputs a stable matching.

For simplicity we'll be assuming that the names of n men and n women are 0, 1, ..., n-1.

Then the menPreferences is a two-dimensional array (a list of lists in Python) of dimensions n by n, where menPreferences[i] contains the list of all women sorted according to their rankings by the man number i. As an example, the man number i likes the best the woman number menPreferences[i][0], and likes the least the woman number menPreferences[i][n-1]. Similarly, the array womenPreferences contains rankings of men by women. For example, womenPreferences[i][0] is the number of man who is the top choice for woman i.

Our function will return a list of length n, where ith element is the number of woman chosen for the man number i.

For convenience we can store

1. unmarriedMen -- the list of currently unmarried men;

2. manSpouse -- the list of current spouses of all man;

3. womanSpouse -- the list of current spouses of all woman;

4. nextManChoice -- contains the number of proposals each man has made.

## See Also:
1. [Simple Proof of the algorithm](https://d3c33hcgiwev3.cloudfront.net/efvWXCCaEeiFIxKh3jdPBg_7a3b7710209a11e88f9c53d16cfdac1d_notes.pdf?Expires=1545955200&Signature=Q1Lh5Y7aqXSpI06TRlGj-0-meGyIFamzqzBAObRcuvnI1Q-xmGDmk0tz~bENkmQ-QI-4NzRMRHjY6Q7aPuOw29mwK8Tajwtj2UQLbVGp~dFgci-DJmxOV617Et38H8L4nPkJ-wNWnWtjpL6mB1ZQDMozboohrZ-1cRIZBC6V5io_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
2. [Original Publication of the algorithm](https://www.jstor.org/stable/2312726)
