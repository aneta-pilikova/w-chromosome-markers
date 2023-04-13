**Vývoj molekulárních markerů pro určení pohlaví u předivky brslenové (_Yponomeuta cagnagella_)**

[Development of molecular markers for sex determination of the spindle ermine moth (_Yponomeuta cagnagella_), in Czech]

Předkládaná diplomová práce má za cíl identifikovat sekvence z pohlavního chromozomu W pomocí k-merové analýzy genomových sekvenačních dat obou pohlaví.
Sekvenací genomové DNA na platformě Oxford Nanopore Technology byla získána data ve formátu FAST5. Ta byla zpracována pomocí skriptu „02_Basecalling“ a kvalita ověřených dat byla ověřena postupem uvedeným ve skriptu „02_Nanoplot.sh“. Skládání genomu (assembly) bylo provedeno podle skriptu „03_Flye“. Kvalita byla ohodnocena pomocí skriptů „04_BUSCO1“ a „05_Quast“.

Druhá a třetí verze genomu byla získána na základě filtrovaných dat a „polishing“ procedur. Filtrace sekvenačních dat na minimální délku sekvencí 5000 bp a 10000 bp a následné vyhodnocení bylo provedeno podle skriptu „06_Nanofilt“. Soubory s filtrovanými daty byly použity pro opravu sekvencí sami sebou, viz skript „07_Canu“. Vytvořený výstup byl použit ve skriptu „08_Flye2“. Byla tak vytvořena dvě genomová assembly, jejichž kvalita byla ohodnocena pomocí skriptů „09_BUSCO2“ a „05_Quast“.

Data získaná sekvenační platformou Illumina ve formátu FASTQ byla nejprve upravena pomocí skriptu „10_FastQC“. Data byla dále rozložena na 15 mery, viz skript „11_Jellyfish“. Další postup se odvíjel podle publikované pipeline Y chromozome Genome Scan (YGS) pipeline (Carvalho a Clark 2013). Pro ověření tohoto přístupu u motýlů (Lepidoptera), kde je heterogametickým pohlavím samice, byla pohlaví v publikovaných skriptech zaměněna. V prvním kroku byla vytvořena bitová pole (bit-arrays), reprezentující 15 mery přítomné v krátkých čteních samců „M“ a také samic „F“, viz skript „12_YGS_trace“. Následně byly extrahovány 15 mery z fragmentů reprezentujících samičí genom získaný výše, a opět uchovány v podobě bit-array, viz skript „13_YGS_contig“. Následně byly pomocí logických operací bit-array porovnány, viz „14_YGS_finalrun“. YGS pipeline byla zopakována pro všechny dostupné kombinace dat.

Následně byl z každé tabulky exportován sloupec a názvem scaffoldu či contigu a příslušné procento validovaných unikátních 15 merů (P_VSC_UK) postupem popsaným v „15_proceeding“. Z této tabulky byl na základě průměrů hodnot P_VSC_UK vytvořen histogram v programu RStudio s využitím skriptu „16_histogram“. Následně byly P_VSC_UK filtrovány s hranicí 75 % napříč všemi analýzami, čímž byly identifikovány fragmenty, které obsahovaly sekvence potenciálně specifické pro chromozom W. Filtrování bylo provedeno v tabulkovém procesoru Microsoft Excel. Tyto fragmenty "YGS_RESULT_W-specific_fragments" byly namapovány na samčí genom z dalšího jedince, který v dosavadní analýze nebyl zahrnut, viz „17_BLAST_proceeding“. Následně byly v kandidátních sekvencích zamaskovány repetice s využitím RepeatMasker (www.repeatmasker.org). K-mery specifické pouze pro samice byly získány podle skriptu „18_F_kmers“ a byly namapovány na kandidátní sekvence „19_Bowtie2“.

Povaha sekvencí byla později ověřena nástrojem DANTE "20_DANTE".
