# Plan van aanpak portfolio-opdracht Stroke

## Doel en deadline

We leveren uiterlijk **zondag 11 oktober 2026** één volledig, netjes gestructureerd en foutloos uitvoerbaar Jupyter-notebook in. Het notebook bevat de EDA, evaluatie, alle verplichte modellen en ensembles, cross-validation, hyperparametertuning, minimaal twee passende technieken voor de sterk ongebalanceerde data, Kaggle-resultaten, een conclusie en advies, en correcte APA- en AI-bronvermeldingen.

Onze interne einddatum is **vrijdag 9 oktober 2026**. Daardoor blijven 10 en 11 oktober beschikbaar voor controle en problemen bij de definitieve inlevering.

## Huidige stand per 25 september 2026

De EDA en het evaluatiehoofdstuk hebben een eerste uitwerking. **3.1 en 3.2 staan klaar voor review**, maar zijn pas definitief afgerond na akkoord van de reviewer en het oplossen van diens bevindingen. De overige verplichte modellen, ensembles en de conclusie zijn nog niet uitgewerkt. Tijn maakte de oorspronkelijke EDA, 1.11 en de eerste KNN-uitwerking. Yorrick schreef **Belangrijkste Bevindingen** en breidde **Niet relevante kolommen** uit.

| Onderdeel | Status | Huidige stand en nog te doen |
| --- | --- | --- |
| Mappen en data | Basis gereed | `train.csv`, `test.csv` en `sample_submission.csv` staan in `data/`. KNN-submissionbestanden staan in de projectmap. |
| Team- en Kaggle-informatie | Minimumeis gehaald | Teamleden en Kaggle-accounts staan in het notebook. De eigen KNN-submission `submission_knn_threshold_fixed.csv` behaalde **F1 0,13071**, boven de vereiste 0,1. Bewaar ook bewijs van de Kaggle-score. |
| Kolombeschrijvingen en EDA | Deels gereed | Basisstatistieken, verdelingen, correlaties, boxplots en aanvullende controles zijn aanwezig. Maak beschrijvingen van alle dummyvariabelen compleet en voeg ontbrekende targetgerichte analyses en datakwaliteitschecks toe. |
| Opschonen en standaardiseren | Deels gereed | ID-verwijdering, dummyredundantie en standaardisatie zijn uitgewerkt. De schaalpipeline wordt gebruikt in de baseline en KNN. Herzie het verwijderen van woongebied: een niet-significante toets bewijst niet dat een kenmerk voor voorspelling nutteloos is. |
| 2.1–2.3 Evaluatie | Uitgewerkt, review nodig | Gestratificeerde split/CV, metricformules, Logistic Regression-baseline en confusion matrix staan in het notebook. Verwijder de resterende placeholder in 2.1 en controleer de uitleg en uitvoer. |
| 3.1 Algemene modelaanpak | Klaar voor review | Gedeelde 5-fold CV-, pipeline-, imbalance- en F1-aanpak is beschreven. Yorrick controleert of de aanpak bij elk later model consequent wordt toegepast. |
| 3.2 K-Nearest Neighbors | Klaar voor review, bevindingen open | Geneste CV/tuning, twee resamplingopties, drempelplot, validatie-F1, confusion matrix, submission en resultaattekst zijn aanwezig. Vul de werking van KNN plus Euclidische en Manhattan-afstand met formule of voorbeeld aan. De submissioncel is nu uitgecommentarieerd terwijl oude uitvoer zichtbaar blijft; herstel dit voor de eindversie. |
| Overige modellen en ensembles | Niet gestart | 3.3–3.7 bevatten placeholders. De Logistic Regression-baseline uit hoofdstuk 2 is nog geen volledige uitwerking van 3.3. |
| Cross-validation, tuning en imbalance | Voor KNN uitgevoerd | KNN vergelijkt RandomOverSampler en RandomUnderSampler binnen de pipeline, met hyperparameters en drempel via CV. Pas dezelfde eisen nog toe op alle overige modellen en ensembles. |
| Conclusie en advies | Niet gestart | Modelvergelijking, beste-modelkeuze, bredere afwegingen en advies aan artsen ontbreken. |
| Codekwaliteit en reproduceerbaarheid | Review nodig | Meerdere cellen zijn uitgevoerd, maar de KNN-submissioncel heeft uitgecommentarieerde code en nog opgeslagen uitvoer. Voer het volledige notebook later vanaf een schone kernel uit en controleer de volgorde, resultaten en PEP8. |
| Bronvermelding en AI-verantwoording | Deels gereed | Technische bronnen zijn toegevoegd; promptnummers, gedeelde links en de volledige APA- en AI-verantwoording zijn nog niet af. |
| README | Bijgewerkt | Bevat nu de voortgang, de behaalde Kaggle-score en de belangrijkste resterende onderdelen. |

## Werkverdeling

De eigenaar schrijft en test het onderdeel. De reviewer controleert de inhoud, code, bronnen en reproduceerbaarheid en moet het onderdeel daarna zelf kunnen uitleggen. Een onderdeel is pas klaar nadat de reviewer akkoord is.

| Onderdeel                                  | Eigenaar              | Reviewer          | Concrete verantwoordelijkheid                                                                                                                                       |
| ------------------------------------------ | --------------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Notebookstructuur en technische integratie | Tijn                  | Yorrick           | Nummering en volgorde bewaken, gedeelde imports/functies beheren en zorgen dat het notebook van boven naar beneden uitvoert.                                        |
| 1.1 t/m 1.8 Bestaande EDA                  | Tijn                  | Yorrick           | Maak de kolombeschrijvingen volledig, voeg targetgerichte analyses en datakwaliteitschecks toe en controleer de conclusies.                                        |
| 1.9 Belangrijkste Bevindingen              | Yorrick               | Tijn              | Bevindingen laten aansluiten op de getoonde analyses en onderscheid maken tussen correlatie en voorspellende waarde.                                                |
| 1.10 Niet relevante kolommen               | Yorrick               | Tijn              | Valideer opschoningskeuzes; baseer featureverwijdering niet alleen op p-waarden; houd identifiers buiten de features.                                               |
| 1.11 Standaardisatie                       | Tijn                  | Yorrick           | Theorie en basispipeline zijn toegevoegd; vul promptgegevens aan en gebruik de pipeline in latere schaalgevoelige modellen.                                        |
| 2 Evaluatie                                | Tijn                  | Yorrick           | Eerste uitwerking en baseline zijn aanwezig. Review 2.1–2.3, verwijder de placeholder in 2.1 en controleer de getoonde metrics en confusion matrix. |
| 3.1 Algemene modelaanpak                   | Tijn                  | Yorrick           | Tekst is klaar voor review. Controleer gedeelde pipeline, lekvrije CV/tuning-opzet en toepasbaarheid op alle modellen; Yorrick houdt het experiment- en Kaggle-log bij. |
| 3.2 K-Nearest Neighbors                    | Tijn                  | Yorrick           | Code, tuning, validatie, confusion matrix en Kaggle-resultaat staan er. Review de methode en resultaten; vul afstandsformules/voorbeeld aan en herstel de uitgecommentarieerde submissioncel. |
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
| **20 september**                      | Notebook herstructureren en werk verdelen | **Afgerond.** Structuur staat en werkverdeling is vastgelegd. |
| **23 september**                      | EDA en preprocessing afronden             | **Deels afgerond.** Standaardisatie en aanvullende opschoningsanalyses zijn toegevoegd. Kolombeschrijvingen zijn aanwezig maar incompleet; bredere targetanalyses en validatie van featureverwijderingen resteren. Afronden uiterlijk 26 september. |
| **25 september**                      | Evaluatiehoofdstuk en baseline afronden   | **Eerste uitwerking aanwezig.** Uiterlijk 26 september review van 2.1–2.3: placeholder verwijderen, berekeningen en interpretatie controleren en de baseline vanaf een schone kernel nalopen. |
| **29 september**                      | KNN, Logistic Regression en SVM afronden  | **KNN en 3.1 staan ter review.** Rond hun reviewpunten af. Werk daarna 3.3 Logistic Regression en 3.4 SVM uit met vereiste theorie, CV, tuning, twee imbalance-aanpakken, validatie en Kaggle-resultaten. |
| **1 oktober**                         | Decision Tree afronden                    | Splitscriteria, pruning, underfitting/overfitting, CV, tuning en imbalance-aanpakken zijn uitgewerkt en getest.                                                                                                                                                                     |
| **4 oktober**                         | Alle ensembles afronden                   | Random Forest, Gradient Boosted Trees, XGBoost en een ensemble van minimaal drie modellen zijn uitgelegd, getuned en vergeleken. Bagging, boosting, sequential/parallel training en voting zijn correct behandeld.                                                                  |
| **6 oktober**                         | Kaggle-fase afronden                      | **Minimum F1 0,1 is al gehaald met KNN (0,13071).** Pas van ieder overig verplicht model en ensemble de beste variant toe op `test.csv`, dien de eigen voorspellingen in en registreer alle lokale en Kaggle-scores. |
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

1. **Uiterlijk 26 september:** Yorrick reviewt 3.1 en 3.2. Controleer vooral de lekvrije CV, de beste parameters en scores, de ontbrekende uitleg van beide afstanden, de uitgecommentarieerde submissioncel en de opgeslagen uitvoer. Tijn verwerkt de bevindingen.
2. Review 2.1–2.3 en de Logistic Regression-baseline: verwijder de placeholder in 2.1 en controleer metricberekeningen, confusion matrix en tekst.
3. Tijn maakt de kolombeschrijvingen volledig, vult targetgerichte analyses en datakwaliteitschecks aan; Yorrick controleert de EDA-conclusies en keuzes over featureverwijdering.
4. Start 3.3 Logistic Regression en 3.4 SVM volgens de werkverdeling. Gebruik de KNN-werkwijze als technisch voorbeeld, maar tune en beoordeel ieder model apart.
5. Houd een gedeeld experimentlog bij met eigenaar, CV-instelling, imbalance-techniek, parameters, lokale F1, Kaggle-F1, submissionbestandsnaam en bewijs van de Kaggle-score van **0,13071**.
6. Voeg bronnen en AI-prompts tijdens het schrijven toe. Gebruik `sample_submission.csv` alleen als formaatvoorbeeld; de labels in submissions moeten uit eigen modellen komen.

## Belangrijkste risico's

- **Omvang:** alleen KNN heeft nu een modeluitwerking en Kaggle-resultaat; Logistic Regression als volledig model, SVM, Decision Tree en de ensembles moeten nog worden gemaakt.
- **Datalekken:** resampling en standaardisatie moeten binnen de cross-validation-pipeline gebeuren, niet vooraf op de volledige trainingsdata.
- **Featureselectie op p-waarden:** de huidige woongebiedsectie verwijdert een feature omdat de chi-kwadraattoets niet significant is. Herzie dit besluit met voorspellende validatie; een niet-significante toets op associatie is op zichzelf geen bewijs dat een variabele de modelprestatie niet kan verbeteren.
- **Verouderde notebookuitvoer:** de KNN-submissioncel is uitgecommentarieerd maar toont nog uitvoer van een eerdere run. Herstel die cel en voer het notebook na afronding van boven naar beneden opnieuw uit; controleer ook tabellen, conclusies en opgeschoonde features.
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
