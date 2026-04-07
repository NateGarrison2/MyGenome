# Trim Adaptors and Poor Quality Sequence with Trimmomatic

Now that we have a good overview of our sequence quality and any issues within our data, we can use Trimmomatic to filter and trim our reads to address these issues.


## Paired Reads

Now that we have run Trimmomatic, we can assess how well the program did in removing poor quality sequences.

My Sg341_1_paired.fastq contains warning levels for:
- Per sequence GC content
- Sequence Length Distribution
<img width="1917" height="980" alt="image" src="https://github.com/user-attachments/assets/2fed2193-dcf5-4e50-84a7-e896cdc7ae11" />
<img width="1110" height="600" alt="image" src="https://github.com/user-attachments/assets/aeaeef45-7940-42ba-99e8-33a99b3145b1" />


My Sg341_2_paired.fastq contains warning levels for:
- Per tile sequence quality
- Per sequence GC content
- Sequence Length Distribution
- Adapter Content

<img width="1919" height="975" alt="image" src="https://github.com/user-attachments/assets/402a1730-9dfb-4697-9b90-6e1a5f8096d4" />
<img width="1110" height="600" alt="image" src="https://github.com/user-attachments/assets/2c56cba5-c62b-43b3-9274-94987d84b9e0" />


## Unpaired Reads

My Sg341_1_unpaired.fastq contains warning levels for:
- Per tile sequence quality
- Per base sequence content
- Per sequence GC content
- Sequence Length Distribution
<img width="1919" height="981" alt="image" src="https://github.com/user-attachments/assets/2fc08aa7-b3c3-4fcf-83c4-c6e8ea5c8d06" />
<img width="1919" height="974" alt="image" src="https://github.com/user-attachments/assets/be9eaa03-5a24-409d-bd68-88cbac8f25cc" />


My Sg341_2_unpaired.fastq contains warning levels for:
- Per tile sequence quality
- Per base sequence content
- Per sequence GC content
- Sequence Length Distribution
- Adapter Content
<img width="1919" height="981" alt="image" src="https://github.com/user-attachments/assets/830304f7-1349-4bd6-b0ab-a883eaab830c" />
<img width="1918" height="973" alt="image" src="https://github.com/user-attachments/assets/bcedca33-2867-4b35-a9b8-7338a032714e" />

## Assessment
Trimmomatic did a great job of removing poor quality sequence in just about everything except the Illumina Universal Adapter content within the Sg341_2_unpaired.fastq file.
