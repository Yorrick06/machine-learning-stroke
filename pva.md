# Plan van aanpak portfolio-opdracht Stroke

## Doel en deadline

We leveren uiterlijk **zondag 11 oktober 2026** één volledig, netjes gestructureerd en foutloos uitvoerbaar Jupyter-notebook in. Het notebook bevat de EDA, evaluatie, alle verplichte modellen en ensembles, cross-validation, hyperparametertuning, minimaal twee passende technieken voor de sterk ongebalanceerde data, Kaggle-resultaten, een conclusie en advies, en correcte APA- en AI-bronvermeldingen.

Onze interne einddatum is **vrijdag 9 oktober 2026**. Daardoor blijven 10 en 11 oktober beschikbaar voor controle en problemen bij de definitieve inlevering.

## Huidige stand per 18 september 2026

Eerlijke inschatting: ongeveer **15-20% van de totale opdracht** is inhoudelijk afgerond. De EDA is voor ongeveer **60%** aanwezig, maar opdracht 2, 3 en 4 zijn nog vrijwel volledig open. Tijn heeft de EDA tot nu toe uitgevoerd. Yorrick heeft de onderdelen **Belangrijkste Bevindingen** en **Niet relevante kolommen** geschreven.

| Onderdeel                     | Status                      | Beoordeling                                                                                                                                                                                                        |
| ----------------------------- | --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Mappen en data                | Gereed als basis            | De drie verwachte csv-bestanden staan logisch in`data/` en hebben de juiste aantallen rijen en kolommen.                                                                                                           |
| Team- en Kaggle-informatie    | Grotendeels gereed          | Teamnaam, namen en Kaggle-accounts staan in het notebook. Een aantoonbare eigen Kaggle-submission en score ontbreken nog.                                                                                          |
| Kolombeschrijvingen           | Deels gereed                | De meeste kolommen worden kort beschreven. Beschrijvingen zijn niet overal volledig; referentiecategorieën van one-hot encoding en bronnen ontbreken.                                                              |
| EDA                           | Deels gereed                | Datatypes, missende waarden, statistieken, klasseverdeling, correlaties en boxplots zijn onderzocht. De relaties met de target zijn nog te oppervlakkig en vooral als lineaire correlatie bekeken.                 |
| Opschonen en standaardiseren  | Nauwelijks gereed           | `id` wordt terecht verwijderd. De uitleg en onderbouwde keuze rond standaardisatie ontbreken, evenals een herbruikbare preprocessing-pipeline.                                                                     |
| Evaluatie en metrics          | Niet gereed                 | Formules/uitleg van metrics, confusion matrix en een uitgewerkt baselinemodel ontbreken.                                                                                                                           |
| Verplichte modellen           | Niet gestart                | KNN, Logistic Regression, SVM, Decision Tree, Random Forest, Gradient Boosted Trees, XGBoost en een eigen ensemble ontbreken.                                                                                      |
| Cross-validation en tuning    | Niet gestart                | Er is nog geen CV, GridSearchCV/RandomizedSearchCV of vergelijking van hyperparameters.                                                                                                                            |
| Omgaan met imbalance          | Niet gestart                | De onbalans is goed herkend, maar minimaal twee technieken per model/ensemble zijn nog niet toegepast of uitgelegd.                                                                                                |
| Conclusie en advies           | Niet gestart                | Modelvergelijking, Kaggle-scores, keuze van het beste model en medisch verantwoord advies ontbreken.                                                                                                               |
| Codekwaliteit                 | Onvoldoende voor eindversie | Alle 15 codecellen hebben opgeslagen uitvoer en geen foutmelding, maar er zijn nog geen zelfgedefinieerde functies of classes. Er zijn dubbele/ongebruikte imports en de structuur is niet volledig genummerd.     |
| Bronvermelding                | Onvoldoende en risicovol    | Het notebook bevat links naar Kaggle-accounts/competitie, maar geen inhoudelijke APA-referenties, AI-promptverwijzingen of referentielijst. Dit moet vroeg worden opgelost vanwege de frauderegels in de opdracht. |
| README en reproduceerbaarheid | Onvoldoende                 | De README bevat alleen een titel. Installatie-instructies, benodigde packages, uitvoervolgorde en teamafspraken ontbreken.                                                                                         |

## Werkverdeling

De eigenaar schrijft en test het onderdeel. De reviewer controleert de inhoud, code, bronnen en reproduceerbaarheid en moet het onderdeel daarna zelf kunnen uitleggen. Een onderdeel is pas klaar nadat de reviewer akkoord is.

| Onderdeel                                  | Eigenaar              | Reviewer          | Concrete verantwoordelijkheid                                                                                                                                       |
| ------------------------------------------ | --------------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Notebookstructuur en technische integratie | Tijn                  | Yorrick           | Nummering en volgorde bewaken, gedeelde imports/functies beheren en zorgen dat het notebook van boven naar beneden uitvoert.                                        |
| 1.1 t/m 1.8 Bestaande EDA                  | Tijn                  | Yorrick           | Bestaande analyse afmaken, relaties met`stroke` verdiepen en kolombeschrijvingen completeren zonder conclusies te overdrijven.                                      |
| 1.9 Belangrijkste Bevindingen              | Yorrick               | Tijn              | Bevindingen laten aansluiten op de getoonde analyses en onderscheid maken tussen correlatie en voorspellende waarde.                                                |
| 1.10 Niet relevante kolommen               | Yorrick               | Tijn              | Verwijderingen inhoudelijk onderbouwen en controleren dat identifiers niet als feature worden gebruikt.                                                             |
| 1.11 Standaardisatie                       | Tijn                  | Yorrick           | Theorie, noodzaak per model en lekvrije toepassing binnen pipelines uitwerken.                                                                                      |
| 2 Evaluatie                                | Tijn                  | Yorrick           | Validatiestrategie, confusion matrix, metricformules, baselinemodel en onderbouwing van F1 uitwerken.                                                               |
| 3.1 Algemene modelaanpak                   | Tijn                  | Yorrick           | Eén gedeelde pipeline en eerlijke CV/tuning-opzet maken. Yorrick houdt het experiment- en Kaggle-log bij.                                                           |
| 3.2 K-Nearest Neighbors                    | Tijn                  | Yorrick           | Theorie, afstanden, standaardisatie, modelcomplexiteit, tuning, imbalance en Kaggle-submission.                                                                     |
| 3.3 Logistic Regression                    | Yorrick               | Tijn              | Werking, loss, gradient descent, rekenvoorbeeld, regularisatie, tuning, imbalance en Kaggle-submission.                                                             |
| 3.4 SVM                                    | Tijn                  | Yorrick           | Werking, formules, rekenvoorbeeld, kernels, loss, regularisatie, tuning, imbalance en Kaggle-submission.                                                            |
| 3.5 Decision Tree                          | Yorrick               | Tijn              | Splitscriteria, pruning, underfitting/overfitting, tuning, imbalance en Kaggle-submission.                                                                          |
| 3.6.1 Random Forest                        | Tijn                  | Yorrick           | Bagging, parallelle training, tuning, imbalance en Kaggle-submission.                                                                                               |
| 3.6.2 Gradient Boosted Decision Trees      | Yorrick               | Tijn              | Boosting, sequentiële training, tuning, imbalance en Kaggle-submission.                                                                                             |
| 3.6.3 XGBoost                              | Yorrick               | Tijn              | Boosting, trainingstijd, tuning, imbalance en Kaggle-submission.                                                                                                    |
| 3.7 Zelf samengesteld ensemble             | Tijn en Yorrick       | Onderlinge review | Tijn bouwt de technische combinatie; Yorrick motiveert modelkeuze en voting. Samen tuning, evaluatie en Kaggle-submission controleren.                              |
| 4 Conclusie en advies                      | Yorrick, daarna Tijn  | Onderlinge review | Yorrick maakt de eerste vergelijking en conclusie. Tijn controleert scores, parameters en medische argumentatie. Samen bepalen zij het uiteindelijke advies.        |
| 5 Bronnen en AI-verantwoording             | Ieder voor eigen werk | Onderlinge review | Iedere auteur voegt bronnen direct toe. Tijn controleert promptverwijzingen bij code; Yorrick controleert de volledige APA-referentielijst en niet-AI-onderbouwing. |
| Definitieve uitvoering en inlevering       | Tijn                  | Yorrick           | Tijn voert het notebook uit vanaf een schone kernel. Yorrick controleert de gerenderde inhoud, submissions en inleverbestanden.                                     |

### Samenwerkingsafspraken

1. Werk niet gelijktijdig in dezelfde notebookcellen. Spreek vooraf af welke sectie ieder op zijn eigen branch bewerkt.
2. De auteur levert per model ook de beste parameters, lokale metrics, confusion matrix, twee imbalance-vergelijkingen en Kaggle-score aan.
3. De reviewer controleert niet alleen taal, maar draait de cellen en legt de methode mondeling terug uit aan de auteur.
4. Bronnen en AI-prompts worden tijdens het schrijven toegevoegd, niet pas aan het einde.
5. Voeg pas samen als het onderdeel zelfstandig draait en geen resultaten uit latere notebookcellen nodig heeft.

## Planning

| Uiterlijk gereed                      | Werkzaamheden                             | Klaar wanneer                                                                                                                                                                                                                                                                       |
| ------------------------------------- | ----------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **20 september**                      | Notebook herstructureren en werk verdelen | **Structuur en verdeling uitgevoerd op 18 september.** Alle hoofdstukken hebben een vaste plek. Uiterlijk 20 september bevestigen beide teamleden de verdeling en starten zij het bron- en promptlog.                                                                               |
| **23 september**                      | EDA en preprocessing afronden             | Iedere kolom is correct uitgelegd; relaties met`stroke` zijn met passende tabellen/visualisaties onderzocht; bevindingen zijn onderbouwd; opschoning en de keuze rond standaardisatie zijn beschreven en in een pipeline verwerkt.                                                  |
| **25 september**                      | Evaluatiehoofdstuk en baseline afronden   | Train/validatiestrategie is zonder datalekken opgezet; confusion matrix, precision, recall, F1 en eventuele aanvullende metrics zijn berekend en uitgelegd; de keuze voor F1 is medisch en technisch onderbouwd.                                                                    |
| **29 september**                      | KNN, Logistic Regression en SVM afronden  | Werking, vereiste wiskunde, rekenvoorbeelden, regularisatie, CV en tuning zijn per model opgenomen. Per model zijn minimaal twee passende imbalance-aanpakken eerlijk binnen CV vergeleken.                                                                                         |
| **1 oktober**                         | Decision Tree afronden                    | Splitscriteria, pruning, underfitting/overfitting, CV, tuning en imbalance-aanpakken zijn uitgewerkt en getest.                                                                                                                                                                     |
| **4 oktober**                         | Alle ensembles afronden                   | Random Forest, Gradient Boosted Trees, XGBoost en een ensemble van minimaal drie modellen zijn uitgelegd, getuned en vergeleken. Bagging, boosting, sequential/parallel training en voting zijn correct behandeld.                                                                  |
| **6 oktober**                         | Kaggle-fase afronden                      | Van**ieder verplicht model en ensemble** is de versie met de beste gevonden hyperparameters op `test.csv` toegepast en als eigen resultaat op Kaggle getest. Alle lokale scores en Kaggle-scores zijn geregistreerd en minimaal één geldige teamsubmission behaalt F1 0,1 of hoger. |
| **8 oktober**                         | Conclusie, advies en bronnen afronden     | Vergelijkingstabel bevat alle modellen en ensembles; beste parameters en scores zijn vermeld; modelkeuze houdt naast prestatie ook rekening met uitlegbaarheid, foutkosten, bias en medische inzetbaarheid; APA-referentielijst en AI-verantwoording zijn compleet.                 |
| **9 oktober**                         | Technische en inhoudelijke eindcontrole   | Notebook draait vanaf een schone kernel volledig van boven naar beneden zonder fouten; code is PEP8-conform en waar zinvol in functies/classes geplaatst; iedere groepsgenoot kan alle code en tekst toelichten.                                                                    |
| **10 oktober**                        | Peer review en definitieve versie         | Beide teamleden hebben de volledige opdrachtchecklist afgevinkt; spelling, figuren, tabellen, links, scores en bronverwijzingen zijn gecontroleerd; definitieve bestanden staan klaar.                                                                                              |
| **11 oktober, ruim voor de deadline** | Inleveren en verifiëren                   | Juiste notebookversie is ingeleverd, vereiste Kaggle-submission staat op naam van het team en de ontvangst/inleverstatus is gecontroleerd.                                                                                                                                          |

## Eisen per onderdeel

### Algemene eisen aan het notebook

- Er wordt precies één net en duidelijk gestructureerd notebook ingeleverd.
- Hoofdstukken en paragrafen zijn genummerd; tekst staat in markdowncellen en uitvoerbare code in codecellen.
- Herhaalde logica staat zo veel mogelijk in zelfgedefinieerde functies. Waar het logisch waarde toevoegt wordt bij voorkeur OOP gebruikt; als een functie duidelijker is, wordt die keuze kort onderbouwd.
- Code voldoet aan PEP8 en bevat nuttige comments die keuzes uitleggen.
- Alle cellen voeren vanaf een schone kernel in de juiste volgorde zonder fouten uit.
- Beide teamleden begrijpen alle code en tekst en kunnen die toelichten.

### 1 Exploratieve Data Analyse en Data Voorbewerking

- Iedere kolom wordt afzonderlijk en correct uitgelegd, inclusief datatype, eenheid/betekenis, one-hot-representatie en eventuele referentiecategorie.
- De minimale voorwaarden voor gebruik met scikit-learn worden beoordeeld: numerieke features, missende/oneindige waarden, vormen van `X` en `y`, targettype en irrelevante identificerende kenmerken.
- Datatypes en passende basisstatistieken worden voor iedere kolom getoond.
- Relaties tussen iedere onafhankelijke variabele en `stroke` worden onderzocht met passende visualisaties. Alleen een correlatiematrix is hiervoor niet voldoende.
- De belangrijkste bevindingen volgen aantoonbaar uit de getoonde resultaten. Correlatie wordt niet gelijkgesteld aan causaliteit of voorspellende waarde.
- Irrelevante rijen en kolommen worden beargumenteerd verwijderd; test-id's blijven beschikbaar voor submissions.
- Standaardisatie wordt uitgelegd, de relevantie per model wordt onderbouwd en eventuele toepassing gebeurt binnen de modelpipeline.

### 2 Evaluatie

- Een zelfgekozen classificatiemodel dient als reproduceerbare baseline.
- Confusion matrix, accuracy, precision, recall en F1-score worden berekend en inhoudelijk uitgelegd. Formules sluiten aan bij true positives, false positives, true negatives en false negatives.
- De keuze voor F1 als Kaggle-metric wordt gekoppeld aan de klasse-onbalans en de balans tussen precision en recall.
- De medische gevolgen van false negatives en false positives worden besproken zonder te claimen dat het model zelfstandig diagnoses kan stellen.

### 3 Algemene eisen voor ieder model en ensemble

- Ieder model krijgt een inhoudelijke uitleg, reproduceerbare code, gestratificeerde cross-validation en hyperparametertuning.
- Voor ieder model/ensemble worden minimaal twee passende technieken voor de ongebalanceerde target toegepast, uitgelegd en eerlijk vergeleken. Resampling vindt alleen binnen de trainingsfolds plaats.
- De beste hyperparameters, gemiddelde CV-F1, validatieresultaten en confusion matrix worden vastgelegd.
- Het model met de beste gevonden hyperparameters wordt toegepast op `test.csv`; de eigen voorspellingen worden in het juiste submissionformaat op Kaggle getest en de score wordt genoteerd.
- Iedere vergelijking gebruikt dezelfde splitsing/CV-opzet en dezelfde primaire metric, tenzij een afwijking expliciet wordt onderbouwd.

### 3.2 K-Nearest Neighbors

- Uitleg bevat afstand, Euclidische afstand en Manhattan-afstand, met formules of een klein rekenvoorbeeld.
- Het belang van standaardisatie wordt uitgelegd en aangetoond.
- De relatie tussen `n_neighbors`, afstandsweging en modelcomplexiteit/regularisatie wordt behandeld.
- Relevante hyperparameters worden getuned en de beste combinatie wordt gerapporteerd.

### 3.3 Logistic Regression

- Werking, sigmoid en loss-functie worden met correcte formules uitgelegd.
- Gradient descent wordt met relevante formules en een eenvoudig doorgerekend voorbeeld uitgelegd.
- Toepasselijke regularisatievormen worden met formules, effecten en relatie tot overfitting behandeld.
- Relevante hyperparameters worden getuned en de beste combinatie wordt gerapporteerd.

### 3.4 SVM

- Werking en relevante wiskunde worden uitgelegd met een rekenvoorbeeld op een klein deel van de dataset.
- Margin, support vectors, kernel en kernel trick worden correct behandeld.
- Loss-functie en regularisatie worden met formules en effecten uitgelegd.
- Relevante hyperparameters worden getuned en de beste combinatie wordt gerapporteerd.

### 3.5 Decision Tree

- Werking en mogelijke splitscriteria worden uitgelegd.
- Pre-pruning en/of post-pruning worden benoemd en gekoppeld aan underfitting en overfitting.
- Relevante hyperparameters worden getuned en de beste combinatie wordt gerapporteerd.

### 3.6 Ensembles

- Random Forest, Gradient Boosted Decision Trees en XGBoost worden alle drie toegepast en uitgelegd.
- Bagging/bootstrap aggregation en boosting worden correct onderscheiden.
- Verschillen in trainingstijd worden onderbouwd met sequential en parallel.
- Ieder ensemble krijgt afzonderlijke CV, imbalance-vergelijking, tuning, beste parameters en Kaggle-score.

### 3.7 Zelf samengesteld ensemble

- Het ensemble bevat minimaal drie modellen.
- De gekozen modellen en de vorm van voting worden inhoudelijk gemotiveerd.
- Cross-validation, imbalance-technieken en tuning worden toegepast; lokale en Kaggle-resultaten worden gerapporteerd.

### 4 Conclusie en advies

- Eén overzichtstabel bevat alle modellen en ensembles, beste parameters, notebookscores en Kaggle-scores.
- Het best presterende model wordt aangewezen en de keuze wordt met resultaten onderbouwd.
- Naast prestatie worden ten minste uitlegbaarheid, foutkosten, robuustheid/generaliseerbaarheid, bias en rekentijd besproken.
- Het advies aan artsen benoemt een model, argumentatie, beperkingen en voorwaarden voor gebruik als beslisondersteuning.

### 5 Bronvermelding en generatieve AI

- Tekst, figuren en overgenomen/aangepaste code hebben passende APA-verwijzingen.
- Tekst wordt geparafraseerd; maximaal 5% van de totale tekst wordt letterlijk overgenomen en letterlijke tekst wordt zichtbaar geciteerd.
- Maximaal 25% van de code wordt letterlijk uit bronnen overgenomen en ook kleine aanpassingen blijven als overname herkenbaar en vermeld.
- Bij generatieve AI staan modelnaam, versie, datum, promptnummer, chattitel en gedeelde link vermeld. Bij een ChatGPT-link is de gebruikersnaam zichtbaar gemaakt via **Share your name**.
- AI-inhoud wordt daarnaast gecontroleerd en ondersteund met een niet-AI-bron.
- Promptverwijzingen staan in relevante markdowncellen en als comments bij code waarbij AI is gebruikt, bijvoorbeeld `# Prompt 1: Titel van de prompt` en `[ChatGPT, 2026. Prompt 1: Titel van de prompt](gedeelde-link)`.
- Het notebook eindigt met één volledige referentielijst in APA-stijl.

### Kaggle-eisen

- Ieder teamlid heeft een Kaggle-account en de teamnaam, namen en gebruikersnamen staan in het notebook.
- Het team heeft minimaal één submission met een eigen getraind model en behaalt minimaal F1 0,1.
- Er worden geen labels of voorspellingen van anderen gebruikt.

## Eerstvolgende acties

1. Tijn rondt de open EDA-punten en standaardisatie af; Yorrick controleert tegelijk of zijn belangrijkste bevindingen nog volledig door de analyses worden gedragen.
2. Tijn maakt één lekvrije `Pipeline`/`imblearn`-werkwijze voor preprocessing, resampling, cross-validation en tuning; Yorrick test deze zelfstandig voordat de modellen worden verdeeld.
3. Maak een gedeeld experimentlog met per model de eigenaar, datasetversie, imbalance-techniek, CV-instelling, parameters, lokale F1, Kaggle-F1 en submissionbestandsnaam.
4. Voeg bronnen en AI-prompts meteen toe tijdens het schrijven. Achteraf reconstrueren is foutgevoelig en vormt hier een serieus beoordelingsrisico.
5. Gebruik de huidige `sample_submission.csv` alleen als formaatvoorbeeld. Maak modelvoorspellingen in aparte, duidelijk benoemde submissionbestanden.

## Belangrijkste risico's

- **Omvang:** er moeten acht modelvarianten/ensembles worden uitgelegd, getuned en vergeleken; het grootste deel is nog niet gestart.
- **Datalekken:** resampling en standaardisatie moeten binnen de cross-validation-pipeline gebeuren, niet vooraf op de volledige trainingsdata.
- **Misleidende evaluatie:** door slechts 1,54% positieve gevallen is accuracy nauwelijks bruikbaar. Rapporteer minimaal precision, recall, F1 en de confusion matrix en bespreek de kosten van false negatives.
- **Bronnen en AI:** ontbrekende verwijzingen kunnen volgens de opdracht als fraude worden gezien. Dit is een harde eis, geen afwerking voor het einde.
- **Medische formulering:** presenteer het model als beslisondersteuning en niet als zelfstandig diagnostisch systeem; bespreek uitlegbaarheid, generaliseerbaarheid, bias en validatie op nieuwe data.

## Definitie van klaar

De opdracht is pas klaar als één nette, genummerde notebook volledig reproduceerbaar uitvoert, alle verplichte inhoud bevat, alle modellen eerlijk vergelijkt, een eigen geldige Kaggle-score van minimaal 0,1 aantoont, correcte bronvermeldingen bevat en door beide teamleden mondeling kan worden toegelicht.

## Controle van dit plan tegen de opdrachtomschrijving

Het plan dekt alle expliciete onderdelen uit de opdrachtomschrijving:

- de harde notebookeisen, samenwerking en PEP8;
- alle gevraagde EDA- en preprocessingstappen;
- metrics, berekeningen, confusion matrix en motivatie van F1;
- KNN, Logistic Regression, SVM en Decision Tree met hun modelspecifieke theorie en wiskunde;
- Random Forest, Gradient Boosted Decision Trees, XGBoost en een ensemble van minimaal drie modellen;
- cross-validation, hyperparametertuning en minimaal twee imbalance-technieken voor ieder model/ensemble;
- toepassing van iedere beste modelvariant op `test.csv` en registratie van Kaggle-resultaten;
- de vergelijkingstabel, beste-modelkeuze, bredere afwegingen en advies aan artsen;
- Kaggle-teamgegevens, een eigen submission en de minimumscore van F1 0,1;
- APA-bronnen, grenzen voor letterlijke overname en de volledige AI-verantwoording.

De toetsmatrijs in `opdracht_info` noemt Portfolio 1 als toetsing van classificatiemodellen en de bijbehorende wiskundige uitleg. Die twee leerdoelen zijn in dit plan zichtbaar afgedekt door zowel implementatie/evaluatie als modelspecifieke formules en rekenvoorbeelden. De toetsmatrijs noemt collegejaar 2024-2025 en wordt daarom alleen aanvullend gebruikt; de opdrachtomschrijving 2026-2027 is leidend.
