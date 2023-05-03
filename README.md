# CompLaplace

We have developed privacy-preserving methods that combine the compressive mechanism and the Laplace mechanism.

This contains the Python codes for our experiments in which we evaluated our mechanisms in terms of accuracy, rank error, and run time.

## Major cons of our methods and future directions

・Need more rigorous evaluation of reconstruction errors in the compressive mechanism.
(Pure differential privacy might not be completely satisfied.  Need to utilize and introduce relaxed concepts of DP(?) (Should consider how to set the threshold between sig and non-sig groups.))

・Need close examination of the distribution of random noise (and sensitivity in the compressive mechanism). (More noise than expected seems to be added to elements in the sig group.)

---> &nbsp; &ensp;  I intend to develop methods that truly satisfy $\epsilon$-differential privacy while varying the noise added to sig and non-sig groups. (Not limited to the compressed sensing technique used in this work. (From the perspective of privacy assuarace, we may not be able to use the information conpressiong techniques with large reconstruction errors.))

(・We should consider other information compression techniques and noise distributions.)

・(2023/05) Probably, more noise than necessary has been added to the significant data, and coupled with reconstruction error in the Compressed Sensing, about half of those statistics become too large, especially for small $\epsilon$ (The other half become too small). As a result, even if $\epsilon$ is close to $0$, we can achieve high accuracy around $50$%, which should not be allowed for privacy assuarance. Although there is room for research to determine how much privacy error is included in the output, this method should not be used, at least for satisfying $(\epsilon, 0)$-differential privacy. However, varying the noise distribution according to the properties of statistics is thought to be important for improving accuracy, so we will continue to examine the use of other probability distributions, not limited to the Laplace distribution. (Maybe the simplest approach is to use the Gumbel distribution or to employ the concept of ${\it smooth\ sensitivity}$.)

## Note

For details of our mechanisms, please see our paper entitled "Privacy-Preserving Statistical Analysis of Genomic Data using Compressive Mechanism with Haar Wavelet Transform" (https://doi.org/10.1089/cmb.2022.0246) published in Journal of Computational Biology.
This study was also presented at Privacy Security Workshop at RECOMB'22.

### Contact
Akito Yamamoto

Division of Medical Data Informatics, Human Genome Center,

the Institute of Medical Science, the University of Tokyo

a-ymmt@ims.u-tokyo.ac.jp
