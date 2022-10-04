# hse22_hw1
Список всех введенных команд:
```
    1  mv -r assembly/ hw1/assembly/
    2  mv assembly/ hw1/assembly/ -r
    3  mc
    4  seqtk sample -s727 assembly/oil_R1.fastq 5000000 > R1_PE.fastq
    5  cd hw1
    6  seqtk sample -s727 assembly/oil_R1.fastq 5000000 > R1_PE.fastq
    7  seqtk sample -s727 assembly/oil_R2.fastq 5000000 > R2_PE.fastq
    8  seqtk sample -s418 assembly/oilMP_S4_L001_R1_001.fastq 1500000 > R1_MP.fastq
    9  seqtk sample -s727 assembly/oilMP_S4_L001_R1_001.fastq 1500000 > R1_MP.fastq
   10  seqtk sample -s727 assembly/oilMP_S4_L001_R2_001.fastq 1500000 > R2_MP.fastq
   11  mkdir fastqc
   12  ls *.fastq | xargs -P 4 -tI{} fastqc -o fastqc {}
   13  mkdir multiqc
   14  multiqc -o multiqc fastqc
   15  mc
   16  platanus_trim R1_PE.fastq R2_PE.fastq
   17  platanus_internal_trim R1_MP.fastq R2_MP.fastq
   18  mc
   19  rm *.fastq
   20  mkdir trimmed_fastq
   21  mv -v *trimmed trimmed_fastq/
   22  mkdir trimmed_fastqc
   23  ls trimmed_fastq/* | xargs -P 4 -tI{} fastqc -o trimmed_fastqc {}
   24  mkdir trimmed_multiqc
   25  multiqc -o trimmed_multiqc trimmed_fastqc
   26  mc
   27  time platanus assemble -o Poil -f trimmed_fastq/R1_PE.fastq.trimmed trimmed_fastq/R2_PE.fastq.trimmed 2> assemble.log &
   28  htop
   29  time platanus scaffold -o Poil -c Poil_contig.fa -IP1 trimmed_fastq/R1_PE.fastq.trimmed trimmed_fastq/R2_PE.fastq.trimmed -OP2 trimmed_fastq/R1_MP.fastq.int_trimmed trimmed_fastq/R2_MP.fastq.int_trimmed 2> scaffold.log &
   30  htop
   31  echo scaffold1_len3834389_cov231 > scaffold_name.txt
   32  seqtk subseq Poil_scaffold.fa scaffold_name.txt > longest_scaffold.fna
   33  time platanus gap_close -o Poil -c Poil_scaffold.fa -IP1 trimmed_fastq/R1_PE.fastq.trimmed  trimmed_fastq/R2_PE.fastq.trimmed -OP2 trimmed_fastq/R1_MP.fastq.int_trimmed trimmed_fastq/R2_MP.fastq.int_trimmed 2> gapclose.log &
   34  echo scaffold1_cov231 > longest_scaffold_gapclosed.txt
   35  seqtk subseq Poil_gapClosed.fa longest_scaffold_gapclosed.txt > longest_scaffold_gapclosed.fna
   36  mkdir github
   37  cd github
   38  echo "# hse22_hw1" >> README.md
   39  git init
   40  git add .
   41  git commit -m 'first commit'
   42  git branch -M main
   43  git remote add origin https://github.com/kirillsbe/hse22_hw1.git
   44  git push -u origin main
   45  git config --global user.email 'skrzzt@gmail.com'
   46  git config --global user.name 'kirillsbe'
   47  git push -u origin main
   48  git status
   49*
   50* git commit -m 'first commit
   51  git push -u origin main
   52  history
```

Ссылка на колаб:
https://colab.research.google.com/drive/19ekB8kQmfHjwc5H0mUV8-oosrOFJRP4b?usp=sharing
![image](https://user-images.githubusercontent.com/91340562/193934703-2a90e6b4-aad2-4ae2-a193-9a8fa9d79142.png)
![image](https://user-images.githubusercontent.com/91340562/193934730-776bc925-affd-4a15-ac33-13b53254b1a7.png)
![image](https://user-images.githubusercontent.com/91340562/193934773-05035539-24a6-470a-afa3-e95ba60e3b7f.png)

Скриншоты не trimmed:
![image](https://user-images.githubusercontent.com/91340562/193935268-d8288edf-e846-477d-ab99-fd8960f111ba.png)
![image](https://user-images.githubusercontent.com/91340562/193935322-12553c2a-557b-48ac-b757-80051b749915.png)
![image](https://user-images.githubusercontent.com/91340562/193935370-d7aed8f6-d4e7-46cf-92c7-20efded0d59e.png)
![image](https://user-images.githubusercontent.com/91340562/193935415-dd44e7e4-498b-417b-b15c-b1cc79937218.png)
![image](https://user-images.githubusercontent.com/91340562/193935453-c1c792d4-b014-44a0-8b9d-a709f262685e.png)

Скриншоты trimmed:
![image](https://user-images.githubusercontent.com/91340562/193935543-09df995a-f284-44d6-b32b-50ce3357be09.png)
![image](https://user-images.githubusercontent.com/91340562/193935583-37c25325-0f3a-49df-b498-eb4760e2bf5a.png)
![image](https://user-images.githubusercontent.com/91340562/193935642-db37dc1e-315c-45fd-ac5f-a48da7015b63.png)
