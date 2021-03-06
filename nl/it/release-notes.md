---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-09"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/docs/services/knowledge-studio/release-notes.html){: new_window}.
{: tip}

# Note sulla release
{: #release-notes}

Sono disponibili le seguenti nuove funzioni e modifiche a {{site.data.keyword.knowledgestudiofull}}.
{: shortdesc}

## Agosto 2018
{: #august2018}

### Nuove funzioni e modifiche
{: #new-august2018}

- Introdotta una nuova opzione per la migrazione automatizzata delle istanze del piano standard dalla piattaforma {{site.data.keyword.IBM_notm}} Marketplace obsoleta alla piattaforma [{{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/blogs/bluemix/2017/12/watson-knowledge-studio-ibm-cloud/){: new_window}. Se hai un'istanza standard nella piattaforma obsoleta, avrai l'opzione di migrarla. Per ulteriori informazioni, vedi [Migrazione a {{site.data.keyword.cloud_notm}}](/docs/services/watson-knowledge-studio/client-migration.html).

## Luglio 2018
{: #july2018}

### Nuove funzioni e modifiche
{: #new-july2018}

- La pagina **Deployed Models** è stata aggiornata per includere i modelli dalle istanze {{site.data.keyword.knowledgestudioshort}} gestiti dai *gruppi di risorse* [IAM ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/docs/iam/users_roles.html){: new_window}, in aggiunta ai modelli gestiti dalle *organizzazioni* [Cloud Foundry ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/docs/iam/cfaccess.html){: new_window}.

   Ciò che viene visualizzato nella pagina Deployed Models dipende dalla [regione ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/docs/resources/services_region.html){: new_window} che ospita la tua istanza {{site.data.keyword.knowledgestudioshort}}. Se la regione supporta le istanze gestite da solo uno dei metodi di gestione dell'accesso, visualizzi una scheda per ogni metodo. I modelli dalle istanze gestite da IAM sono elencate nella scheda **Resource Groups**. I modelli dalle istanze gestite da Cloud Foundry sono elencate nella scheda **Organizations**.

  Se la regione supporta le istanze gestite da solo uno dei metodi di gestione dell'accesso, visualizzi solo un elenco di modelli, perché viene applicato solo un metodo di gestione dell'accesso.

   Per visualizzare la pagina **Deployed Models**, dal menu **Settings** nella barra del menu in alto a destra, fai clic su **Manage deployed models**. Per informazioni sull'annullamento della distribuzione dei modelli nella pagina **Deployed Models**, consulta [Annullamento della distribuzione dei modelli di machine learning](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) e [Annullamento della distribuzione dei modelli basati sulla regola](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).

- La navigazione è stata modificata per un migliore allineamento con il flusso di lavoro di {{site.data.keyword.knowledgestudioshort}}. Inoltre, è stata riorganizzata la seguente funzionalità:

    - Nella versione precedente, la gestione dei dizionari era inclusa come parte della pagina Pre-annotators. Ora, la gestione dei dizionari si trova nella pagina Dictionaries nella sezione Assets della navigazione.
    - Nella versione precedente, la funzionalità di annotazione umana era distribuita tra le schede Mentions, Relations e Coreferences nella sezione Document Annotation della navigazione. Ora, la funzionalità è unita alla pagina Annotation Tasks nella sezione Machine Learning Model della navigazione.
    - Per gestire le attività di annotazione umana, nella versione precedente, trovavi la scheda Tasks nella pagina Assets & Tools > Documents. Ora, aggiungi le attività e gestisci le attività esistenti nella pagina Annotation Tasks nella sezione Machine Learning Model della navigazione. 
    - Nella versione precedente, le pagine Rules, Regex e Dictionaries erano pagine separate nella sezione Document Annotation della navigazione. Ora, la funzionalità è unita alla pagina Rules nella sezione Rule-based Model della navigazione.

    Per ulteriori dettagli sulle modifiche alla navigazione, consulta la Figura 1 e la Tabella 3.

![Schermate della precedente navigazione (lato sinistro) e della nuova navigazione (lato destro).](images/nav3-0718.svg "Schermate della navigazione precedente e della nuova navigazione. I dettagli delle modifiche sono elencati nella Tabella 3 e nel testo precedente.") Figura 1. Schermate della precedente navigazione (lato sinistro) e della nuova navigazione (lato destro).

| Funzione | Ubicazione precedente | Ubicazione corrente |
|---------|--------------------------|----------------------|
| Attività di annotazione | Assets & Tools > Documents > Tasks | Machine Learning Model > Annotation Tasks |
| Scheda Coreferences | Document Annotation | Machine Learning Model > Annotation Tasks > task > annotation set > document |
| Pagina Dictionaries (gestione) | Assets & Tools > Pre-annotators > Manage Dictionaries | Assets |
| Scheda Dictionaries (associazione alle classi del modello basato sulla regola) | Document Annotation | Rule-based Model > Rules |
| Pagina Documents | Assets & Tools | Assets |
| Pagina Entity Types | Assets & Tools | Assets |
| Scheda Mentions | Document Annotation | Machine Learning Model > Annotation Tasks > task > annotation set > document |
| Pagina Performance | Model Management | Machine Learning Model |
| Pagina Pre-annotators | Assets & Tools | Machine Learning Model > Pre-annotation |
| Scheda Regex  | Document Annotation | Rule-based Model > Rules |
| Pagina Relation Types | Assets & Tools | Assets |
| Scheda Relations | Document Annotation | Machine Learning Model > Annotation Tasks > task > annotation set > document |
| Scheda Rules | Document Annotation | Rule-based Model |
| Scheda Tasks | Assets & Tools > Documents | Machine Learning Model > Annotation Tasks |
| Pagina Versions (modello di machine learning) | Model Management | Machine Learning Model |
| Pagina Versions (modello basato sulla regola) | Model Management | Rule-based Model |
{: caption="Tabella 3. Modifiche alla navigazione (luglio 2018)" caption-side="top"}

## Maggio 2018
{: #may2018}

### Nuove funzioni e modifiche
{: #new-may2018}

- È stato risolto un problema di configurazione che ha causato la mancata visualizzazione delle istanze del servizio nella regione di Sydney nella regione Stati Uniti Sud.
- Nella finestra Deploy Model, se la regione di cui stai eseguendo la distribuzione supporta sia i *gruppi di risorse* {{site.data.keyword.iamlong}} che gli *spazi* Cloud Foundry, per visualizzare l'elenco, dovrai scegliere il metodo di gestione dell'accesso utilizzato dalla tua istanza del servizio. Per ulteriori informazioni su Cloud Foundry e {{site.data.keyword.iamshort}}, vedi [Resource Groups and Access Management ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/blogs/bluemix/2017/12/resource-groups-access-management/){: new_window}.
- È stata aggiunta l'impostazione di raccolta dei dati nella pagina Service Details. Per ulteriori informazioni sulla raccolta dati, consulta [Risoluzione dei problemi, supporto e FAQ](/docs/services/watson-knowledge-studio/troubleshooting.html#content)
- È stato aggiunto il supporto lingua per il cinese (tradizionale).
- Gli utenti che dispongono del ruolo Admin possono ora visualizzare il numero di aree di lavoro utilizzate. Queste informazioni sono disponibili nella pagina Service Details.
- {{site.data.keyword.alchemylanguagefull}} non è più disponibile per la distribuzione dei modelli. Per informazioni, consulta [Retirement of {{site.data.keyword.alchemyapishort}} service ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/blogs/bluemix/2017/03/bye-bye-alchemyapi/){: new_window}.
- Ora, se elimini uno spazio di lavoro, ti verrà richiesto di confermare l'azione. Ci auguriamo che questa conferma impedisca delle cancellazioni accidentali.
- La documentazione include alcuni nuovi dettagli sulla privacy dei dati. Ulteriori informazioni in [Sicurezza informatica](/docs/services/watson-knowledge-studio/information-security.html).

## Aprile 2018
{: #april2018}

### Nuove funzioni e modifiche
{: #new-april2018}

- Il piano gratuito di {{site.data.keyword.knowledgestudioshort}} è stato sostituito con il piano Lite. Per ulteriori informazioni, vedi [Go Lite with Watson {{site.data.keyword.knowledgestudioshort}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/blogs/bluemix/2018/04/go-lite-watson-knowledge-studio/){: new_window}.

## Marzo 2018
{: #march2018}

### Nuove funzioni e modifiche
{: #new-march2018}

- È disponibile una pagina **Deployed Models** dove puoi visualizzare tutti i modelli {{site.data.keyword.knowledgestudioshort}} distribuiti ai servizi negli spazi a cui hai accesso. Per visualizzare la pagina **Deployed Models**, dal menu **Settings** nella barra del menu in alto a destra, fai clic su **Manage deployed models**. Per informazioni sull'annullamento della distribuzione e sulla visualizzazione dei modelli nella pagina **Deployed Models**, consulta [Annullamento della distribuzione dei modelli di machine learning](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) e [Annullamento della distribuzione dei modelli basati sulla regola](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).
- È ora disponibile una traduzione in francese dell'interfaccia {{site.data.keyword.knowledgestudioshort}}.
- {{site.data.keyword.alchemylanguagefull}} non è più disponibile come pre-annotatore. Invece di {{site.data.keyword.alchemylanguageshort}}, puoi utilizzare {{site.data.keyword.nlushort}} per pre-annotare i tuoi documenti. Per ulteriori informazioni, vedi [Inizio dell'annotazione](/docs/services/watson-knowledge-studio/preannotation.html).

## Dicembre 2017
{: #december2017}

### Nuove funzioni e modifiche
{: #new-december2017}

- {{site.data.keyword.knowledgestudioshort}} è stato lanciato in {{site.data.keyword.cloud_notm}}. Per informazioni sulla pianificazione e il processo di migrazione, consulta [Migrazione a {{site.data.keyword.cloud_notm}}](/docs/services/watson-knowledge-studio/client-migration.html).
- Navigazione riprogettata. Per i dettagli sulle modifiche alla navigazione, consulta la [Tabella 2](#september2017) nelle note sulla release di settembre 2017.
- Aggiunto {{site.data.keyword.nlufull}} come pre-annotatore.
- Aggiunte le impostazioni di gestione dell'archiviazione e dell'utente alla pagina Service Details. Per informazioni sull'aggiunta di utenti, vedi [Assemblaggio di team](/docs/services/watson-knowledge-studio/team.html). Per informazioni sull'impostazione dei limiti di archiviazione, vedi [Risoluzione dei problemi > Problemi di spazio di archiviazione](/docs/services/watson-knowledge-studio/troubleshooting.html#storage).
- Aggiunta una pagina Performance per la valutazione della qualità del modello e come guida su come migliorare la qualità.

## Novembre 2017
{: #november2017}

### Modifiche
{: #new-november2017}

- Corretto un problema per cui mancavano alcune annotazioni della relazione nel corpus scaricato.
- Corretto un problema per cui un modello non poteva essere ritirato dalla distribuzione se il suo stato era **None**.
- Corretto un problema per cui il modello non poteva essere valutato in coreano.

## Ottobre 2017
{: #october2017}

### Modifiche
{: #new-october2017}

- Corretto il problema con il pulsante **Export** che non veniva abilitato finché non aggiornavi la finestra del browser nella release {{site.data.keyword.Bluemix_notm}} [sperimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental).
- Corrette le descrizioni a comparsa e le etichette in modo che corrispondano alle modifiche dei termini _carica_ e _scarica_ nella release {{site.data.keyword.Bluemix_notm}} [sperimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental). Questi termini vengono utilizzati invece di _importa_ e _esporta_ quando si fa riferimento ai sistemi tipo, ai documenti e ai dizionari.
- Corretto il ritardo nell'aggiornamento delle descrizioni nella pagina {{site.data.keyword.knowledgestudioshort}} User Account Management nella release {{site.data.keyword.Bluemix_notm}} [sperimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental).
- Nella sezione di pre-annotazione dell'interfaccia, sono state fatte un paio di modifiche alla GUI per chiarire la funzionalità del modello di machine learning, del modello basato sulla regola, del dizionario e di {{site.data.keyword.alchemylanguagefull}}. Modificata l'etichetta del pulsante da **Run** a **Pre-annotate**, modificato il titolo della finestra da **Run Annotator** a **Run Pre-annotation** e modificato il messaggio di errore per chiarire che non puoi aggiornare le annotazioni automatizzate dopo che gli annotatori umani hanno annotato i documenti.
- Per i progetti o gli spazi di lavoro che utilizzano i tokenizer basati sul dizionario, è stato corretto un problema che mostrava le frasi vuote se importavi i documenti senza il ground truth.

## Settembre 2017
{: #september2017}

### Nuove funzioni e modifiche
{: #new-sept17}

- È stata rilasciata una nuova esperienza utente di frontend per {{site.data.keyword.knowledgestudioshort}} su {{site.data.keyword.Bluemix}} come un servizio [sperimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental). Le modifiche includono una navigazione riorganizzata e una nuova pagina di analisi delle prestazioni del modello. Per un riepilogo delle modifiche alla navigazione, consulta la tabella nei problemi noti.
- Aggiunto il supporto lingua per il cinese (semplificato) e l'olandese.

### Problemi noti
{: #issues-sept17}

- Per un modello basato sulla regola, dopo che associ le classi e i tipi di entità, il pulsante **Export** non è abilitato finché non aggiorni la finestra del browser.
- Per la release {{site.data.keyword.Bluemix_notm}} [sperimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental), una parte della terminologia della documentazione non corrisponde alla nuova interfaccia. La documentazione corrisponde all'interfaccia nel {{site.data.keyword.IBM_notm}} Marketplace. I seguenti termini sono stati modificati nella release [sperimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental):

| Termine nel {{site.data.keyword.IBM_notm}} Marketplace | Termine in {{site.data.keyword.Bluemix_notm}} | Note |
|----------|----------|----------|
| _progetto_ | _spazio di lavoro_ | Questo termine è stato modificato perché anche {{site.data.keyword.Bluemix_notm}} utilizza il termine _progetto_ |
| _importa_ e _esporta_ | _carica_ e _scarica_ | Viene ora fatto riferimento ai termini _importa_ e _esporta_ con _carica_ e _scarica_ quando utilizzati nei termini dei documenti e dei tipi di entità. Il termine _esporta_ viene ancora utilizzato quando si fa riferimento all'esportazione di un modello alle applicazioni come {{site.data.keyword.watson}} Explorer. |
{: caption="Tabella 1. Modifiche alla terminologia della versione {{site.data.keyword.Bluemix_notm}}" caption-side="top"}

- Per la release {{site.data.keyword.Bluemix_notm}} [sperimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental), alcuni passi dell'attività della documentazione non corrispondono nella nuova interfaccia. La documentazione corrisponde all'interfaccia nel {{site.data.keyword.IBM_notm}} Marketplace. La seguente tabella riepiloga le modifiche alla navigazione della release [sperimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental):

| Funzione | Ubicazione nel {{site.data.keyword.IBM_notm}} Marketplace | Ubicazione in {{site.data.keyword.Bluemix_notm}}
|----------|----------|----------|
|Scheda Annotator Component | Navigazione principale | Non esiste più |
|Tabella Confusion Matrix (dalla scheda Statistics) | Annotator Component > Details | Model Management > Performance > Detailed Statistics link |
|Scheda Dictionaries | Navigazione principale | Assets & Tools > Pre-annotators |
|Pagina Dictionary Mapping | Annotator Component | Assets & Tools > Pre-annotators |
|Sheda Entity Types | Type System | Assets & Tools > Entity Types |
|Ground Truth Editor | Human Annotation | Scheda Document Annotation |
|Sheda Ground Truth Editor Settings | Human Annotation | Settings > Document Annotation Settings |
|Modelli, esecuzione ed esportazione | Annotator Component | Model Management > Versions |
|Scheda Rules | Navigazione principale | Document Annotation > Rules |
|Scheda Statistics | Annotator Component > Details | Model Management > Performance |
|Tabella Summary (dalla scheda Statistics) | Annotator Component > Details | Model Management > Performance > Detailed Statistics link |
|Scheda Type Mapping (dal modello basato sulla regola) | Annotator Component > Details | Model Management > Versions > Rule-based model type mapping |
{: caption="Tabella 2. Modifiche alla navigazione della versione {{site.data.keyword.Bluemix_notm}}" caption-side="top"}

## Luglio 2017
{: #july2017}

- Corretto un errore che, in alcuni casi, faceva scomparire l'intestazione
- Applicati gli aggiornamenti di sicurezza ai componenti dell'infrastruttura

## Giugno 2017
{: #june2017}

- Migliorata la stabilità per la gestione di dati molto grandi in determinate condizioni
- Corretto un problema con un errore di giudizio

## Maggio 2017
{: #may2017}

- Aggiunta la capacità di ridenominare vari oggetti, come i progetti, le serie di documenti e così via
- Aggiunta la capacità di distribuire i modelli NLU a regioni {{site.data.keyword.Bluemix}} specifiche
- Migliorate le prestazioni per la visualizzazione di tabelle molto grandi di IAA
- Corretti errori minori
- Applicate le correzioni alla sicurezza

## Aprile 2017
{: #april2017}

- Migliorata la stabilità di {{site.data.keyword.knowledgestudioshort}} Premium
- Aggiunta l'analisi dell'utilizzo delle metriche di business

## Release precedenti ad aprile 2017

Consulta [{{site.data.keyword.IBM_notm}} tech note #1986001 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.ibm.com/support/docview.wss?uid=swg21986001){: new_window}.
