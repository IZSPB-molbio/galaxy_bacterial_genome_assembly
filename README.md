# Analisi genomi batterici su Galaxy Europe

<!-- TOC START min:2 max:3 link:true asterisk:false update:true -->
- [Introduzione](#introduzione)
- [Bacterial genome assembly - IZSPB](#bacterial-genome-assembly---izspb)
    - [Workflow overview](#workflow-overview)
    - [Preparazione read dataset](#preparazione-read-dataset)
    - [Avviare il workflow](#avviare-il-workflow)
    - [Output](#output)
<!-- TOC END -->

## Introduzione

Per analizzare i dati di sequenziamento di genomi batterici viene usato il workflow "**imported: Bacterial genome assembly - IZSPB**"già importato nell'account parisi.izspb@gmail.com su usegalaxy.eu, che segue gli stessi step della pipeline usata su ReCaS.

**Nota**: fra i workflow dell'account parisi.izspb@gmail.com ce n'é un altro chiamato "**Bacterial genome assembly - IZSPB**", ma **non** va usato in quanto il sopracitato workflow è il più aggiornato.

## Bacterial genome assembly - IZSPB

### Workflow overview

- QC filtering con fastp
- assemblaggio con SPADES
- annotazione CDS con PROKKA
- AMR detection con ABRicate
- Sequence typing con MLST (nota: lo schema viene selezionato automaticamente dal tool)
- Report con MultiQC, statistiche su
    - QC filtering
    - assemblaggio (QUAST)

### Preparazione read dataset

Eseguire la stessa procedura per caricare file fastq.gz e creare una collection come spiegato [qui](https://github.com/IZSPB-molbio/galaxy_covid_genome_analysis#caricamento-collection). 

### Avviare il workflow

- Selezionare (dal menù in alto bordato in blu) "Workflow"
- Cliccare sul tasto Play blu sulla destra del workflow "COVID-19: variation analysis on ARTIC PE data"

Apparirà la schermata per impostare il workflow.

- "Paired collection": dovrebbe comparire automaticamente la collection di read appena generata.

A questo punto il workflow sarà pronto per essere avviato tramite il pulsante Play blu in alto a destra.

### Output

La pipeline produrrà una serie di output. Quelli più essenziali per capire la buona riuscita del run sono:

- **MultiQC Webpage** che riporta varie statistiche su read e assemblaggio, campione per campione. Purtroppo solo per PROKKA l'estrazione delle info non funziona bene.
- **ABRicate on collection** contiene, campione per campione, i risultati di ABRicate, mentre **ABRicate summary** è un report complessivo.
- **MLST** riporta i risultati del sequence typing.
- **SPAdes on collection #: scaffolds (fasta)** contiene un file per ogni campione con gli scaffold assemblati.
