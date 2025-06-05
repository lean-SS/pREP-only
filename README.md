                 _________    _________   ________                                         
                |    ___  |  |  _______| |  ____  |                     __                 
         _____  |   |   |  | |  |        |  |   |  |   _____   ______  |  | __     __
        |  __ | |   |___|  | |  |______  |  |___|  |  |  _  | |   _  | |  ||  |   |  |
        | |  | ||   __    /  |   ______| |    ____/   | | | | |  | |  ||  ||  |   |  |
        | |__| ||   | |   |  |  |        |   |        | | | | |  | |  ||  ||  |___|  |
        |  ___/ |   |  |   | |  |______  |   |  ====  | |_| | |  | |  ||  | |_____   |
        |  |    |___|   |___||_________| |___|        |_____| |__| |__||__|   ____|  |
        |__|                                 (or pepperoni)                  |_______/

                Screening tool for Acinetobacter baumannii plasmid Rep proteins.        
                
pREP-only: Screening tool for Acinetobacter baumannii plasmid Rep proteins. 
Introduction:
The first function of this mini-script was written to utilise the AcinetobacterPlasmidTyping 
database, whereby Rep protein sequences from each rep types were downloaded and sorted 
according to their classification/nomenclature by Lam et al (2023) and Lam & Hamidian (2024). 

The second function of the same script works to screen for R3 type plasmid or fragments in 
draft genomes, using an example plasmid backbone - i.e., the (more) commonly seen R3 type 
plasmid backbone harbouring the oriV-abkBA-tonB gene composition (NCBI accession of example 
used: CP007578.1). This part is optional to the user and can be omitted, provided the 
A. baumannii plasmid has been identified prior. 

Credits: 
Lam et al. 2023. "Detection and Typing of Plasmids in Acinetobacter baumannii using rep 
Genes Encoding Replication Initiation Proteins." Microbiol Spectr 14;11(1):e0247822.

Lam, Margaret M. C., and Mehrad Hamidian. 2024. “Examining the Role of 
Acinetobacter baumannii Plasmid Types in Disseminating Antimicrobial Resistance.” npj 
Antimicrobials and Resistance 2(1).

Up for a tad more reading? See README.rst for backstory. 

Prerequisite:
BLAST-legacy/BLAST
via Bioconda
    conda install bioconda::blast-legacy
    
via Brew
    brew install blast
    
then, 

    git clone https://github.com/leanSS/pREPonly.git 
    cd pREPonly
    chmod +x pREPonly
    
Command line options:
./pREPonly -h

                 _________    _________   ________                                         
                |    ___  |  |  _______| |  ____  |                     __                 
         _____  |   |   |  | |  |        |  |   |  |   _____   ______  |  | __     __
        |  __ | |   |___|  | |  |______  |  |___|  |  |  _  | |   _  | |  ||  |   |  |
        | |  | ||   __    /  |   ______| |    ____/   | | | | |  | |  ||  ||  |   |  |
        | |__| ||   | |   |  |  |        |   |        | | | | |  | |  ||  ||  |___|  |
        |  ___/ |   |  |   | |  |______  |   |  ====  | |_| | |  | |  ||  | |_____   |
        |  |    |___|   |___||_________| |___|        |_____| |__| |__||__|   ____|  |
        |__|                                 (or pepperoni)                  |_______/

                Screening tool for Acinetobacter baumannii plasmid Rep proteins.        

    Function: 
    ./pREPonly -h 				        Help page
    ./pREPonly -query -db			        Screens for Rep proteins
    ./pREPonly -split -slice -query -db			Screens for R3-type plasmids and report
    
    ----------------------------------------------------------------------------------
    | Database used in this mini tool was taken from Lam & Hamidian (2024).          |
    | Citation: Lam, Margaret M. C., and Mehrad Hamidian. 2024.                      |
    | “Examining the Role of Acinetobacter baumannii Plasmid Types in Disseminating  |
    | Antimicrobial Resistance.” npj Antimicrobials and Resistance 2(1).             |
    ----------------------------------------------------------------------------------   

Example run:
In both options, the query (i.e., your sequences) should be nucleotide sequences in  
.fasta/.fna/.fa format.  

Option 1: If the plasmid has already been identified and only determination of Rep type required. 
./pREPonly -query pModel1.fasta -db Abau_plasmid-REPs_db

Searching for plasmid Rep... Please wait
Rep protein search completed successfully. Results are in 'results.txt'.

|   Query Filename   |    Best Plasmid Hit     |  pident   | length   |mismatch| gapopen |  evalue  |
|--------------------|-------------------------|-----------|----------|--------|---------|----------|
|    pModel1.fasta   |  pSP304_rep3-Aci3-r3T5  | 100.000   |    307   |    0   |    0   |    0.0 |


Option 2: If the plasmid has yet to be identified, this line detects R3 plasmid or its fragment(s). 
./pREPonly -split -slice -query mock_dna.fasta -db R3_Example-Frame_db  
Just split it! Screening FASTA for plasmid sequences... Please wait
Split n' Slice! Extracting plasmid nucleotide locations from resultsN.txt:
20	3386	4057 
20	7968	8679

Output files:
result.txt			Output from Rep protein screening (prot)
resultN.txt			Containing match to example R3-type plasmid (nucl)



                                                                 _______________
                                                               /*  '.           |  ___  
                                                        .----.   *  |            |/  /_
            Thank you for using pREPonly (pepperoni)!  | *    | *   |            |    _'.
                                                       :    * :   * .,,,,,,,,,,,,|'._'.
                                                       :._*_..: .../__________..| 
