# CompLaplace

We have developed privacy-preserving methods that combine the compressive mechanism and the Laplace mechanism.

**Our method could be used if we can assume that the top and the rest (e.g., significant and non-significant SNP groups) rarely vary between neighboring datasets. (2023/06)**

This contains the Python codes for our experiments in which we evaluated our mechanisms in terms of accuracy, rank error, and run time.

## Comments (Summary of below discussion) (2023/08)

The finding from this study is that, when data can be divided into two groups and we can assume that the partitioning does not vary between the neighboring datasets, the output accuracy may increase by adding different noise to each group. In this study, by adding larger noise to the significant group (while satisfying the same $\epsilon$-differential privacy) using the compressive mechanism, we achieved high accuracy especially when $\epsilon$ was small.

In the future, using this study as a starting point, we intend to develop a highly accurate method that satisfies $\epsilon$-differential privacy without assumptions on partitioning by smoothly varying the noise distribution around a threshold.

Further directions include a close examination of the conditions under which assumptions about data partitioning are valid, the establishment of new methods for quantitatively evaluating the quality of $\epsilon$-DP mechanism (not just accuracy/error evaluation), and the development of privacy concepts that go beyond differential privacy.

## Major cons of our methods and future directions

・When we can assume that the partitioning does not vary between neighboring datasets (for example, when we can assume that the set of significant SNPs does not change even if a single individual in the analysis varies), our method can satisfy $\epsilon$-differential privacy; therefore, we can use it to improve accuracy when the required privacy level is high.

### The below discussion is for the case when we cannot make the assumption on the partitioning.

・Need more rigorous evaluation of reconstruction errors in the compressive mechanism.
(Pure differential privacy might not be completely satisfied. Need to utilize and introduce relaxed concepts of DP(?) (Should consider how to set the threshold between significant and non-significant groups.))

・Need a close examination of the distribution of random noise (and sensitivity in the compressive mechanism). (More noise than expected seems to be added to elements in the sig group.)

---> &nbsp; &ensp;  I intend to develop methods that truly satisfy $\epsilon$-differential privacy while varying the noise added to sig and non-sig groups. (Not limited to the compressed sensing technique used in this work. (From the perspective of privacy assuarace, we may not be able to use the information compressing techniques with large reconstruction errors.))

(・We should consider other information compression techniques and noise distributions.)

・**(2023/05)** Probably, more noise than necessary has been added to the significant data, and coupled with reconstruction error in the Compressed Sensing (as briefly mentioned in Conclusion), about half of those statistics become too large, especially for small $\epsilon$ and large $K$ (The other half become too small). As a result, even if $\epsilon$ is close to $0$, we can achieve high accuracy around $50$%, which should not be allowed for privacy assuarance. Although there is room for research to determine how much privacy error is included in the output, this method should not be used, at least for satisfying $(\epsilon, 0)$-differential privacy; The shortcomings in our proof are that we rely too much on the value of the upper bound of ${sensitivity}$ in the Compressive Mechanism (p.4, l.7 in the Supplemental Material) and that **we do not take into account the reconstruction errors**. (Actually, the experimental results in this study indicate that we cannot use a simple Compressed Sensing algorithm for the case where the assumption on the partitioning cannot be made, not our method is truly advisable.) However, varying the noise distribution according to the properties of statistics is expected to be important for improving accuracy, so we will continue to examine the use of other probability distributions, not limited to the Laplace distribution. (Maybe the simplest approach is to employ the concept of ${\it smooth\ sensitivity}$.)

(・It would be extremely important to add no more noise than necessary, i.e., to add only the minimal amount of noise as possible, both in terms of accuracy and privacy assurance.)

**・While this study was kind of a proof-of-concept, we intend to develop more reliable methods by investigating better information compression techniques and considering varying noise distributions smoothly at the boundary to truly satisfy differential privacy.**

・As for the shortcomings of the proof about that our method is $\epsilon$-differentially private, I suppose that we might be able to correct them by making some assumptions/conditions appropriately. (For example, if the sig and non-sig groups are "sufficiently" far apart (i.e., if we can assume that there is no difference in the top group between neighboring datasets (as briefly mentioned in page 6 of the paper)), our method can be used (because we do not have to consider the case mentioned in the latter part of the proof).) However, we should at least carefully verify the experimental results and reconsider the concept of privacy.

(・Is it possible to develop privacy-preserving methods that maintain a certain accuracy regardless of the privacy level (like the results in this study)? (It doesn't matter whether they use differential privacy or not.))

## Note

For details of our mechanisms, please see our paper entitled "Privacy-Preserving Statistical Analysis of Genomic Data using Compressive Mechanism with Haar Wavelet Transform" (https://doi.org/10.1089/cmb.2022.0246) published in Journal of Computational Biology. [Supplemental Material](https://www.liebertpub.com/doi/suppl/10.1089/cmb.2022.0246) provides the proofs of our theorems and other supplemental information.
This study was also presented at Privacy and Security Workshop at RECOMB'22.

### Contact
Akito Yamamoto

Division of Medical Data Informatics, Human Genome Center,

the Institute of Medical Science, the University of Tokyo

a-ymmt@ims.u-tokyo.ac.jp
