move the correct barcodes (62 and 63) to new folder  
```samtools fastq m84151_250401_153316_s2.hifi_reads.bc2062.bam > bc2062.fastq```  
```samtools fastq m84151_250401_153316_s2.hifi_reads.bc2063--bc2063.bam > bc2063.fastq```  
```cat bc2062.fastq bc2063.fastq > Bger_hifi_all.fastq```  
run hifiasm  
```nohup hifiasm -o BgerKwizda.asm -t 32 Bger_hifi_all.fastq > BgerKwizda.asm.log 2>&1 &```  
  
Hifiasm purges haplotig duplications by default. For inbred or homozygous genomes, you may disable purging with option -l0.  
```nohup hifiasm -o BgerKwizda_inbreed.asm -t 32 Bger_hifi_all.fastq > BgerKwizda_inbreed.asm.log 2>&1 &``` 


after assembly is done, convert .gfa to fasta  
```awk '/^S/{print ">"$2"\n"$3}' BgerKwizda.asm.bp.p_ctg.gfa > BgerKwizda.asm.bp.p_ctg.fa```
same with the phased haplotypes  
```awk '/^S/{print ">"$2"\n"$3}' BgerKwizda.asm.bp.hap1.p_ctg.gfa > BgerKwizda.asm.bp.hap1.p_ctg.fa
awk '/^S/{print ">"$2"\n"$3}' BgerKwizda.asm.bp.hap2.p_ctg.gfa > BgerKwizda.asm.bp.hap2.p_ctg.fa```
index
```samtools faidx BgerKwizda.asm.bp.p_ctg.fa``` 
