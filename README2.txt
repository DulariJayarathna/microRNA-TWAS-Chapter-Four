smr_software=/home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/Software/smr_Linux
eQTL_dir=/home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/ncRNA-eQTL/Endometrial

${smr_software} --eqtl-summary ${eQTL_dir}/EndCa_Cis_FDR.txt  --matrix-eqtl-format --make-besd --out /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/SMR_besd/Original/EndCa_Cis
${smr_software} --eqtl-summary ${eQTL_dir}/ColCa_Trans_FDR.txt  --matrix-eqtl-format --make-besd --out /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/SMR_besd/Original/ColCa_Trans

${smr_software} --bfile /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/LDRef/LDREF/1000G.EUR.ch1-22 --gwas-summary /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/GWAS/CoCa/CoCa_gwas.ma --beqtl-summary /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/SMR_besd/Original/ColCa/ColCa_Trans --peqtl-smr 0.05 --peqtl-heidi 0.05 --out /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/Output/ColCa_Trans
awk -F"\t" '{print $2,$4,$5,$6,$7,$8,$9,"NA"}' BCAC_meta-analysis-erpos.prectgvl.rsids.ctgvl.checked > BCAC_gwas_erpos.ma
awk -F"\t" '{print $2,$4,$5,$6,$7,$8,$9,"NA"}' BCAC_meta-analysis-nerpos.prectgvl.rsids.ctgvl.checked > BCAC_gwas_erneg.ma
${smr_software} --bfile /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/LDRef/LDREF/1000G.EUR.ch1-22 --gwas-summary /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/GWAS/BrCa/BCAC_gwas_erpos.ma --beqtl-summary /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/SMR_besd/Original/BRCA_Cis --peqtl-smr 0.05 --peqtl-heidi 0.05 --out /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/Output/BRCA_Cis_erpos
${smr_software} --bfile /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/LDRef/LDREF/1000G.EUR.ch1-22 --gwas-summary /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/GWAS/BrCa/BCAC_gwas_erneg.ma --beqtl-summary /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/SMR_besd/Original/BRCA_Cis --peqtl-smr 0.05 --peqtl-heidi 0.05 --out /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/Output/BRCA_Cis_erneg
awk '{ if ($19<0.05) { print } }' BRCA_Cis_erpos.ma > BRCA_Cis_erpos_Sig
awk '{ if ($20>0.05) { print } }' BRCA_Cis_erpos_Sig > BRCA_Cis_erpos_Sig_HEIDI



${smr_software} --bfile /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/LDRef/LDREF/1000G.EUR.ch1-22 --gwas-summary /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/GWAS/BrCa/BCAC_gwas.ma --beqtl-summary /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/SMR_besd/Original/BRCA_Trans --peqtl-smr 0.05 --peqtl-heidi 0.05 --out /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/Output/BRCA_Trans
${smr_software} --bfile /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/LDRef/LDREF/1000G.EUR.ch1-22 --gwas-summary /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/GWAS/BrCa/BCAC_gwas_erpos.ma --beqtl-summary /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/SMR_besd/Original/BRCA_Trans --peqtl-smr 0.05 --peqtl-heidi 0.05 --out /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/Output/BRCA_Trans_erpos
${smr_software} --bfile /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/LDRef/LDREF/1000G.EUR.ch1-22 --gwas-summary /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/GWAS/BrCa/BCAC_gwas_erneg.ma --beqtl-summary /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/SMR_besd/Original/BRCA_Trans --peqtl-smr 0.05 --peqtl-heidi 0.05 --out /home/dulari/Desktop/lyra/GENETICS/SMR-HEIDI/Output/BRCA_Trans_erneg


echo -e "SNP\tA1\tA2\tfreq\tb\tse\tp\tn" > file2.txt && cat OvCa_gwas.ma >> file2.txt
