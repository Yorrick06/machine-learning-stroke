# Plan van aanpak portfolio-opdracht Stroke

## Doel en deadline

We leveren uiterlijk **zondag 11 oktober 2026** één volledig, netjes gestructureerd en foutloos uitvoerbaar Jupyter-notebook in. Het notebook bevat de EDA, evaluatie, alle verplichte modellen en ensembles, cross-validation, hyperparametertuning, minimaal twee passende technieken voor de sterk ongebalanceerde data, Kaggle-resultaten, een conclusie en advies, en correcte APA- en AI-bronvermeldingen.

Onze interne einddatum voor de inhoudelijke conceptversie is **vrijdag 9 oktober 2026**. Op 10 oktober controleren we de volledige uitvoering en maken we de definitieve versie. 11 oktober blijft de buffer voor noodzakelijke correcties en inlevering. Dit is een krappe planning: verplichte onderdelen afronden gaat nu vóór extra score-experimenten.

## Huidige stand per 8 oktober 2026

De EDA, evaluatie, KNN, Logistic Regression, SVM en Decision Tree hebben een uitwerking. Random Forest heeft theorie en trainingscode, maar nog geen vastgelegde resultaten. **3.1 en 3.2 staan klaar voor review**, met concrete open punten hieronder. Gradient Boosted Decision Trees, XGBoost, het eigen ensemble en de conclusie zijn nog placeholders. Uitgewerkt betekent dus niet automatisch gecontroleerd of afgerond.

De lange trainingscellen staan **bewust als Raw**, zodat ze tijdens het werken niet bij iedere Run All opnieuw trainen. Dat is geen onbedoelde fout. Wel moeten de definitieve code en resultaten straks reproduceerbaar zijn; zie de afspraken over de eindcontrole.

| Onderdeel | Status | Huidige stand en nog te doen |
| --- | --- | --- |
| Mappen en data | Basis gereed | Train-, test- en voorbeeldsubmission staan in `data/`. Submissionbestanden voor KNN, LR, SVM en Tree zijn aanwezig. Leg ook de benodigde pakketversies vast. |
| Team- en Kaggle-informatie | Minimumeis gehaald | Teamleden en Kaggle-accounts staan in het notebook. De eigen KNN-submission `submission_knn_threshold_fixed.csv` behaalde **F1 0,13071**, boven de vereiste 0,1. Bewaar ook bewijs van de Kaggle-score. |
| Kolombeschrijvingen en EDA | Deels gereed | Basisstatistieken, verdelingen, correlaties, boxplots en aanvullende controles zijn aanwezig. Maak beschrijvingen van alle dummyvariabelen compleet en voeg ontbrekende targetgerichte analyses en datakwaliteitschecks toe. |
| Opschonen en standaardiseren | Deels gereed | ID-verwijdering, dummyredundantie en standaardisatie zijn uitgewerkt. De schaalpipeline wordt gebruikt in de baseline en KNN. Herzie het verwijderen van woongebied: een niet-significante toets bewijst niet dat een kenmerk voor voorspelling nutteloos is. |
| 2.1–2.3 Evaluatie | Uitgewerkt, review nodig | Gestratificeerde split/CV, metricformules, Logistic Regression-baseline en confusion matrix staan in het notebook. Verwijder de resterende placeholder in 2.1 en controleer de uitleg en uitvoer. |
| 3.1 Algemene modelaanpak | Klaar voor review | Gedeelde 5-fold CV-, pipeline-, imbalance- en F1-aanpak is beschreven. Yorrick controleert of de aanpak bij elk later model consequent wordt toegepast. |
| 3.2 K-Nearest Neighbors | Klaar voor review | Werking, Euclidische/Manhattan-formules en een klein rekenvoorbeeld zijn toegevoegd. De submission gebruikt nu de juiste modelvariabele via de gedeelde functie. Review de inhoud en controleer na uitvoering de resultaten en nieuwe CSV. |
| 3.3 Logistic Regression | Uitgewerkt, review nodig | Theorie, gradient-descentvoorbeeld, tuning en opgeslagen resultaten zijn aanwezig. Controleer of de ingestelde regularisatie werkelijk overeenkomt met `l1_ratio` en de gebruikte scikit-learn-versie. Controleer daarna parameters, uitvoer en submission. |
| 3.4 SVM | Theorie aangevuld, volledige training nog nodig | Het rekenvoorbeeld gebruikt drie gecontroleerde datasetrijen; de voorbeeldgewichten zijn duidelijk onderscheiden van getrainde gewichten. Labels −1/+1, hinge loss en beslissingsscore zijn verduidelijkt. Code voor beste parameters, drempel, CV-F1, validatiemetrics en confusion matrix is aanwezig. De volledige SVM-gridsearch is bij deze wijziging niet uitgevoerd; definitieve getallen blijven dus open. |
| 3.5 Decision Tree | Uitgewerkt, resultaten controleren | Theorie, pruning en trainingscode zijn aanwezig. Leg de daadwerkelijk gekozen parameters, CV-score, lokale metrics en confusion matrix vast en koppel deze aan de submission. |
| 3.6.1 Random Forest | Theorie en code aanwezig | Controleer de uitleg van voorspellingen: scikit-learn middelt de kansen van de bomen. Training, resultaten, imbalance-vergelijking en Kaggle-submission moeten nog worden afgerond. |
| 3.6.2, 3.6.3 en 3.7 | Nog uit te werken | Gradient Boosted Decision Trees, XGBoost en een eigen ensemble van minimaal drie modellen bevatten nog placeholders. Theorie, code, tuning, resultaten en submissions ontbreken. |
| Cross-validation, tuning en imbalance | Aanpak aanwezig, vergelijking incompleet | KNN is lokaal reproduceerbaar gecontroleerd. Ook LR, SVM, Tree en RF hebben tuningcode. Rapporteer per model de vergelijking van minimaal twee imbalance-technieken, beste parameters en CV-resultaten; alleen de winnende sampler noemen is onvoldoende. |
| Conclusie en advies | Niet gestart | Modelvergelijking, beste-modelkeuze, bredere afwegingen en advies aan artsen ontbreken. |
| Codekwaliteit en reproduceerbaarheid | Gedeelde functies toegevoegd, eindcontrole nodig | `toon_resultaten` toont modelinstellingen en alle validatiemetrics. `maak_submission` hertraint de gekozen pipeline, houdt de drempel vast en controleert features, klassen en id-volgorde. KNN/LR/SVM/Tree hebben korte aanroepen in Raw-cellen; oude uitvoer van die submissioncellen en de KNN-KeyboardInterrupt zijn verwijderd. Nieuwe CSV-namen eindigen op `_nieuw`; bestaande Kaggle-bestanden blijven behouden. Een volledige schone run blijft nodig. |
| Bronvermelding en AI-verantwoording | Deels gereed | Technische bronnen zijn toegevoegd; promptnummers, gedeelde links en de volledige APA- en AI-verantwoording zijn nog niet af. |
| README | Later actualiseren | Werk na afronding de voortgang en uitvoerinstructies bij. Het README is met deze PvA-update niet aangepast. |

### Controle van de aanvullingen op 8 oktober

- KNN-afstandsformules en het rekenvoorbeeld zijn toegevoegd. Het SVM-voorbeeld gebruikt drie echte datasetrijen; scores en hinge loss zijn nagerekend.
- De gedeelde resultaat-/submissionfuncties zijn getest met kleine runs voor KNN, SVM, Tree en RF op 300 datasetrijen. De tests controleren ook de vaste drempel en het weigeren van verkeerde features of id-volgorde. Dit zijn technische tests, geen definitieve modelscores.
- Notebookstructuur en Python-syntax zijn gecontroleerd. Bestaande modelgrids en preprocessingkeuzes zijn niet veranderd. Er zijn bij deze wijziging geen nieuwe submission-CSV's aangemaakt en geen bestanden op Kaggle ingediend.
- Nog open: volledige trainingen uitvoeren, definitieve uitvoer opslaan, nieuwe submissions controleren/indienen en AI-promptgegevens voor deze aanvullingen invullen. De volledige schone eindrun en onderlinge review blijven nodig.

### Vastgelegde Kaggle-resultaten

Dit zijn de public scores uit de aangeleverde Kaggle-resultaten, geen nieuwe metingen. De minimumscore geldt voor minimaal één eigen teammodel, niet voor ieder model afzonderlijk.

| Submission | Public F1 |
| --- | --- |
| KNN, eerste versie | 0,09785 |
| KNN, eerdere drempelversie | 0,04968 |
| KNN, vaste gekozen drempel | **0,13071** |
| Logistic Regression | 0,09352 |
| SVM | 0,09497 |
| Decision Tree | 0,07272 |

KNN voldoet al aan de minimumscore. Voor de andere modellen blijft een volledige, eerlijke uitwerking vereist. Een hogere public score is geen bewijs dat een model geschikt is voor medische inzet.

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
| 3.2 K-Nearest Neighbors                    | Tijn                  | Yorrick           | Afstandsformules/voorbeeld en submissionkoppeling zijn aangevuld. Yorrick reviewt de uitwerking; Tijn controleert de resultaten en CSV na uitvoering. |
| 3.3 Logistic Regression                    | Yorrick               | Tijn              | Bestaande theorie en code reviewen; pakketversie en regularisatie controleren; zo nodig opnieuw trainen en de resultaten/submission actualiseren. |
| 3.4 SVM                                    | Tijn                  | Yorrick           | Rekenvoorbeeld en formule-uitleg staan er. Tijn voert de volledige training, resultaat-/matrixcellen en submission uit; Yorrick controleert theorie, instellingen en scoreherkomst. |
| 3.5 Decision Tree                          | Yorrick               | Tijn              | Bestaande uitwerking reviewen; gekozen pruning/parameters, lokale resultaten, imbalance-vergelijking en submission vastleggen. |
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

### Omgaan met lange trainingsruns

- Tijdens het werken mogen dure trainingscellen Raw blijven. Zet alleen de benodigde trainingscellen tijdelijk terug naar Code wanneer je een model opnieuw wilt trainen.
- Noteer na een run de pakketversies, random seeds, beste parameters, gekozen drempel, CV-score, validatiemetrics en submissionbestandsnaam. Opgeslagen uitvoer moet bij de huidige code horen.
- Voer eerst de imports, data/preprocessing, split en gedeelde functiecel onder 3.1 uit. Na een modeltraining toont `toon_resultaten` de actuele uitkomsten. Zet daarna de bijbehorende Raw-plot/matrix/submission naar Code en voer deze uit. De submissionfunctie traint opnieuw op alle ontwikkeldata, maar doet geen nieuwe drempelzoektocht.
- Bestaande Kaggle-scores blijven gekoppeld aan de oude bestanden. Geef een nieuwe submission pas een score na daadwerkelijk indienen; testuitvoer op een kleine dataset telt niet als definitief modelresultaat.
- Houd de grids klein en inhoudelijk onderbouwd. Geneste CV met drempeltuning vermenigvuldigt de rekentijd; start zware runs tijdig en voorkom onnodig tegelijk draaien op dezelfde computer.
- Voor de definitieve versie zijn benodigde trainings- en submissioncellen uitvoerbaar. Plan op 10 oktober één volledige run vanaf een schone kernel, inclusief de lange training. Een Run All die Raw-training overslaat bewijst niet dat het hele notebook reproduceerbaar is.
- Als die volledige run niet binnen de beschikbare tijd past, verklein de zoekruimte vóór de eindcontrole en rapporteer de opnieuw verkregen resultaten. Niet alleen oude uitvoer laten staan of verplichte modellen overslaan.

## Planning

| Uiterlijk gereed                      | Werkzaamheden                             | Klaar wanneer                                                                                                                                                                                                                                                                       |
| ------------------------------------- | ----------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **8 oktober** | Bestaande onderdelen herstellen en ontbrekende ensembles starten | Tijn: EDA/evaluatie, KNN-reviewpunten, SVM-voorbeeld en RF. Yorrick: LR/Tree-review en GBDT/XGBoost. Samen: grids op haalbare rekentijd controleren, pakketversies vastleggen en bronnen bijhouden. |
| **9 oktober, overdag** | Verplichte modeluitwerkingen en trainingen afronden | Eigenaren leveren per model theorie, tuning, twee imbalance-aanpakken, beste parameters, CV-score, validatiemetrics en confusion matrix. Dure runs zijn gestart met voldoende tijd voor herstel. |
| **9 oktober, einde dag** | Eigen ensemble en inhoudelijke conceptversie gereed | Tijn bouwt het ensemble van minimaal drie modellen; Yorrick motiveert samenstelling/voting en begint de vergelijking/conclusie. Alle verplichte secties hebben inhoud, geen lege placeholders. Ontbrekende resultaten worden expliciet gemarkeerd en uiterlijk de volgende ochtend aangevuld. |
| **10 oktober, ochtend** | Resultaten, submissions, conclusie en bronnen compleet | Eigenaren registreren de laatste Kaggle-resultaten. Yorrick maakt vergelijkingstabel, advies en APA-lijst af; Tijn controleert parameters, scoreherkomst, AI-verwijzingen en uitvoerbaarheid. README actualiseren. Geen nieuwe vrijblijvende score-experimenten meer. |
| **10 oktober, middag en avond** | Volledige uitvoering, onderlinge review en definitieve versie | Tijn draait het volledige notebook vanaf een schone kernel met benodigde Code-cellen; Yorrick controleert inhoud en opdrachtchecklist. Beide begrijpen alle onderdelen. Na correcties horen code, uitvoer, tekst en submissions bij dezelfde versie. |
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
- Leg ook de gekozen beslisdrempel, gebruikte kans/beslissingsscore en pakketversies vast. De submission is aantoonbaar afkomstig uit de beschreven modelvariant; de drempel wordt niet gekozen op basis van verborgen Kaggle-labels of steeds op de public leaderboard afgestemd.
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

1. **8 oktober — Tijn, review Yorrick:** afstandsformules/voorbeeld, submissionkoppeling en gedeelde functies zijn toegevoegd. Review nu 3.1/3.2 en controleer de echte modeluitvoer en nieuwe CSV na training. Verwijder ook de placeholder in 2.1 en controleer de baseline.
2. **8–9 oktober — Yorrick, review Tijn:** controleer LR-regularisatie tegen de gebruikte pakketversie. Leg voor LR en Tree de echte beste parameters, CV/validatiemetrics en vergelijking van imbalance-technieken vast. Opnieuw trainen als de code/configuratie wijzigt.
3. **8–9 oktober — Tijn, review Yorrick:** het SVM-rekenvoorbeeld en de formule-uitleg zijn aangevuld. Voer de volledige SVM-gridsearch uit, bekijk de resultaatuitvoer en confusion matrix en maak de nieuwe submission via de functie. Vul RF-resultaten aan en corrigeer de uitleg van kansmiddeling.
4. **Uiterlijk 9 oktober — Yorrick:** werk GBDT en XGBoost uit. **Tijn en Yorrick:** maak daarna het eigen ensemble met minimaal drie modellen, gemotiveerde voting, CV, tuning en twee imbalance-aanpakken.
5. **Uiterlijk 9 oktober — Tijn/Yorrick:** maak alle kolombeschrijvingen en targetgerichte EDA compleet. Toon noodzakelijke datakwaliteitschecks. Herzie te sterke conclusies over lage correlaties, woongebied en onbekende rookstatus; onbekend betekent niet automatisch nooit gerookt. Featurekeuzes mogen niet op de labels van de holdout worden afgestemd.
6. **Uiterlijk 10 oktober, ochtend — ieder eigen modellen, Yorrick overzicht:** leg per variant parameters, drempel, CV-instelling, imbalance-techniek, lokale metrics, submissionbestandsnaam en Kaggle-score/bewijs vast. Rond hoofdstuk 4, bronnen, AI-prompts en README af. Gebruik `sample_submission.csv` uitsluitend als formaatvoorbeeld.
7. **10 oktober — Tijn uitvoering, Yorrick review:** maak benodigde cellen uitvoerbaar en voer één volledige schone run uit. Controleer ook id-volgorde en 8.388 voorspellingen per submission, geen oude foutuitvoer, geen undefined variabelen en geen verschillen tussen gerapporteerde resultaten en code.
8. **Alleen als bovenstaande af is:** onderzoek betere scores met kleine, vooraf gekozen CV-experimenten, bijvoorbeeld een lineaire SVM met undersampling en aangepaste `C`. Vergelijk op dezelfde CV-opzet; een lokale verbetering garandeert geen hogere Kaggle-score. De minimumscore is al gehaald.

## Belangrijkste risico's

- **Omvang en tijd:** LR, SVM en Tree zijn toegevoegd, maar GBDT, XGBoost, het eigen ensemble, conclusie en bronverantwoording zijn nog niet compleet. Verplichte inhoud en gecontroleerde resultaten gaan vóór extra scoreverbetering.
- **Rekentijd:** uitgebreide grids met geneste drempeltuning kunnen uren duren. Raw-cellen voorkomen herhaald trainen tijdens het werken, maar vervangen geen definitieve uitvoering. Beperk zoekruimtes en start de eindrun tijdig.
- **Versieafhankelijkheid:** LR-regularisatie kan anders werken dan bedoeld als `l1_ratio`, penalty en de pakketversie niet overeenkomen. Maak de configuratie expliciet en controleer waarschuwingen voordat resultaten worden overgenomen.
- **Datalekken:** resampling en standaardisatie moeten binnen de cross-validation-pipeline gebeuren, niet vooraf op de volledige trainingsdata.
- **Featureselectie op p-waarden:** de huidige woongebiedsectie verwijdert een feature omdat de chi-kwadraattoets niet significant is. Herzie dit besluit met voorspellende validatie; een niet-significante toets op associatie is op zichzelf geen bewijs dat een variabele de modelprestatie niet kan verbeteren.
- **Verouderde notebookuitvoer:** de submissioncellen zijn opgeschoond, maar andere opgeslagen uitvoer kan nog van eerdere runs zijn. De volledige grids zijn bij deze wijziging niet opnieuw uitgevoerd. Zorg bij de eindcontrole dat modelvariabelen, parameters, drempels, uitvoer en ingediende bestanden naar dezelfde variant verwijzen.
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
