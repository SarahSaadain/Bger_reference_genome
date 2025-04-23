move the correct barcodes (62 and 63) to new folder  
```samtools fastq m84151_250401_153316_s2.hifi_reads.bc2062.bam > bc2062.fastq```  
```samtools fastq m84151_250401_153316_s2.hifi_reads.bc2063--bc2063.bam > bc2063.fastq```  
```cat bc2062.fastq bc2063.fastq > Bger_hifi_all.fastq```  
after assembly is done, convert .gfa to fasta  
```nohup hifiasm -o BgerKwizda.asm -t 32 Bger_hifi_all.fastq > BgerKwizda.asm.log 2>&1 &```  
