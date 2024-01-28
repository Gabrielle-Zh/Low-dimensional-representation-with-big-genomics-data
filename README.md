# Low-dimensional-representation-with-big-genomics-data

## Preprocess.ipynb
### This file is responsible for data preprocessing and it achieves following tasks:
1. Cut reads and reference bins into kmers. There are two kmer size, 15 and 20.
2. Create two distinct kmer lists based on all kmers from reads and reference bins. The number of distinct kmer with kmer size = 15 is 72530 and the number of distinct kmer with kmer size = 20 is 77751
3. Use previously created kmer lists to encode read and reference bins. For kmer size as 15, shape of reads' one-hot encoding result is 72530 * 2000; shape of reference bins' one-hot encoding result is 72530 * 500. For kmer size as 20, shape of reads' one-hot encoding result is 77751 * 2000; shape of reference bins' one-hot encoding result is 77751 * 500.
4. One-hot encoding results are sparse matrix. So, you can use sparse vectors to store the results for storage save.
5. Store the one-hot encoding results in sparse vector format

## _sparse_ files
They are one-hot encoding results in sparse vector format from Preprocess.ipynb, respectively read_sparse_15, ref_sparse_15, read_sparse_20, and ref_sparse_20. These four files are the input of Minhash_Comparison_Result.ipynb

## Minhash_Comparison_Result.ipynb
### This file achieves the following tasks:
1. Use the minHash function to achieve dimensionality reduction. Three permutation numbers: 500, 1000, 2000
2. Apply parallel function in the hash function.
3. Calculate the Jaccard similarity between reads and bins and find the most similar bin for every read
4. Compare the alignment result with the benchmark and analyze the results. Use Pearson correlation and mean squared error to quantify the difference.
5. Try different combinations of kmer size and permutation number to explore how they influence the quality of prediction results.
