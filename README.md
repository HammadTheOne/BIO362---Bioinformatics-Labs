# BIO362---Bioinformatics-Labs
#Bioinformatics Labs Python Code

#GWAS dataset and Pandas DataFrame

import pandas as pd

my_gwas = pd.read_table('gwas_data.txt')

gwas_columns = my_gwas.columns

print(my_gwas.head())
print(my_gwas.shape)
print(gwas_columns)

import pandas as pd

gwas_2 = pd.read_table('gwas_data.txt')
print(gwas_2.head())

base_comp_df = gwas_2[['CHR', 'BP', 'BASE']]

print(base_comp_df.head())

gwas_data = pd.read_table('gwas_data.txt')

gwas_data_fixed = gwas_data.assign(log_p = -(numpy.log10(gwas_data.P)))


print(gwas_data_fixed.head())

candidate_snps = gwas_data_fixed[gwas_data_fixed.log_p >= 5]

candidate_snp_count = candidate_snps.shape

print(candidate_snps)
print(candidate_snp_count)


import pandas as pd 

def p_hist(gwas_df, num_bins: int):
    return gwas_df.P.hist(bins = num_bins)

p_hist(gwas_data, 200)


import pandas as pd

def manhattan(gwas_df, chromosome):
    '''Pre-condition: chromosome in gwas_df.CHR '''
    my_df = gwas_df[gwas_df.CHR == chromosome]
    my_df2 = my_df.assign(log_p = -(numpy.log10(my_df.P)))
    
    my_plot = my_df2.plot(x = 'BP', y = 'log_p', kind = 'scatter')
    
    return my_plot


manhattan(gwas_data, 3)
