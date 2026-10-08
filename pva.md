# Plan van aanpak portfolio-opdracht Stroke

## Doel en deadline

We leveren uiterlijk **zondag 11 oktober 2026** één volledig, netjes gestructureerd en foutloos uitvoerbaar Jupyter-notebook in. Het notebook bevat de EDA, evaluatie, alle verplichte modellen en ensembles, cross-validation, hyperparametertuning, minimaal twee passende technieken voor de sterk ongebalanceerde data, Kaggle-resultaten, een conclusie en advies, en correcte APA- en AI-bronvermeldingen.

Onze interne einddatum voor de inhoudelijke conceptversie is **vrijdag 9 oktober 2026**. Op 10 oktober controleren we de volledige uitvoering en maken we de definitieve versie. 11 oktober blijft de buffer voor noodzakelijke correcties en inlevering. Dit is een krappe planning: verplichte onderdelen afronden gaat nu vóór extra score-experimenten.

## Huidige stand per 8 oktober 2026

De EDA, evaluatie, KNN, Logistic Regression, SVM, Decision Tree en Random Forest hebben een uitwerking en opgeslagen resultaten. **3.1 en 3.2 staan klaar voor review**, met concrete open punten hieronder. Gradient Boosted Decision Trees en XGBoost hebben nu theorie, keuzes, tuningcode, resultaat-/plotcellen en een submissionaanroep. Hun volledige runs en resultaatinterpretaties ontbreken nog. Het eigen ensemble en de conclusie zijn nog placeholders. De LR-gridsearch bevat een bevestigde regularisatiefout die nog moet worden hersteld. Uitgewerkt of uitgevoerd betekent dus niet automatisch gecontroleerd of afgerond.

Na de laatste volledige run zijn de **43 bestaande codecellen uitgevoerd**, met oplopende uitvoernummers en zonder opgeslagen foutmeldingen. De daarna toegevoegde GBDT-/XGBoost-cellen hebben nog geen volledige modeluitvoer. De submissioncellen van KNN, GBDT en XGBoost staan Raw en worden bij Run All overgeslagen. Raw gebruiken om herhaald trainen te voorkomen blijft toegestaan tijdens het werken. De eindversie moet wel volledig reproduceerbaar zijn; zie de afspraken over de eindcontrole.

| Onderdeel                             | Status                                            | Huidige stand en nog te doen                                                                                                                                                                                                                                                                                                                                                                             |
| ------------------------------------- | ------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mappen en data                        | Basis gereed                                      | Train-, test- en voorbeeldsubmission staan in`data/`. Oude submissions staan in `submission_file/`; drie nieuwe submissions staan in de projectroot. De 11 aanwezige CSV's hebben het juiste formaat en dezelfde id-volgorde als de testdata. Leg pakketversies en uitvoerinstructies vast.                                                                                                          |
| Team- en Kaggle-informatie            | Minimumeis gehaald                                | Teamleden en Kaggle-accounts staan in het notebook. De eigen KNN-submission`submission_knn_threshold_fixed.csv` behaalde **F1 0,13071**, boven de vereiste 0,1. Bewaar ook bewijs van de Kaggle-score.                                                                                                                                                                                           |
| Kolombeschrijvingen en EDA            | Deels gereed                                      | Basisstatistieken, verdelingen, correlaties, boxplots en aanvullende controles zijn aanwezig. Maak beschrijvingen van alle dummyvariabelen compleet en voeg ontbrekende targetgerichte analyses en datakwaliteitschecks toe.                                                                                                                                                                             |
| Opschonen en standaardiseren          | Deels gereed                                      | ID-verwijdering, dummyredundantie en standaardisatie zijn uitgewerkt. Alle vijf getunede modellen gebruiken de gedeelde schaalpipeline. Herzie de woongebiedkeuze: geen significant verband bewijst niet dat een feature nutteloos is. Deze keuze is bovendien op alle ontwikkellabels gemaakt, vóór de holdoutsplit.                                                                                  |
| 2.1–2.3 Evaluatie                    | Uitgewerkt, review nodig                          | Gestratificeerde split/CV, metricformules, Logistic Regression-baseline en confusion matrix staan in het notebook. Verwijder de resterende placeholder in 2.1 en controleer de uitleg en uitvoer.                                                                                                                                                                                                        |
| 3.1 Algemene modelaanpak              | Klaar voor review                                 | Gedeelde 5-fold CV-, pipeline-, imbalance- en F1-aanpak is beschreven. Yorrick controleert of de aanpak bij elk later model consequent wordt toegepast.                                                                                                                                                                                                                                                  |
| 3.2 K-Nearest Neighbors               | Uitgevoerd, klaar voor review                     | Formules, voorbeeld, beste parameters, metrics en confusion matrix zijn aanwezig. De nieuwe submission ontbreekt nog doordat de submissioncel Raw is. Voer alleen die cel uit als het getrainde model nog in de kernel staat.                                                                                                                                                                            |
| 3.3 Logistic Regression               | Uitgevoerd, correctie nodig                       | CV-F1 0,1468 en validatie-F1 0,1497 zijn opgeslagen. De waarschuwing bevestigt dat`l1_ratio` wordt genegeerd bij de huidige L2-penalty: L1 en L2 zijn dus niet echt vergeleken. Herstel de configuratie en herhaal de LR-training, resultaten en submission.                                                                                                                                           |
| 3.4 SVM                               | Uitgevoerd, review nodig                          | Voorbeeld, training, metrics, confusion matrix en nieuwe CSV zijn aanwezig. Beste CV-F1 van de vijf modellen: 0,1567. Corrigeer de verouderde markdown die zegt dat resultaten ontbreken; vergelijk imbalance-aanpakken en registreer de nieuwe Kaggle-score.                                                                                                                                            |
| 3.5 Decision Tree                     | Uitgevoerd, review nodig                          | Parameters, metrics, confusion matrix en nieuwe CSV zijn aanwezig. Leg uit dat`max_depth=5` pre-pruning toepast en dat de gekozen `ccp_alpha=0` geen post-pruning toevoegt. De nieuwe CSV is identiek aan de oude.                                                                                                                                                                                   |
| 3.6.1 Random Forest                   | Uitgevoerd, submission ontbreekt                  | Parameters, metrics en confusion matrix zijn aanwezig. Maak nog een submissionaanroep en dien het bestand in. Corrigeer de theorie: scikit-learn middelt boomkansen, in plaats van alleen harde meerderheidsstemmen. Bespreek de imbalance-vergelijking.                                                                                                                                                 |
| 3.6.2 GBDT en 3.6.3 XGBoost | Uitgewerkt, volledige runs en review nodig | Theorie, keuzeonderbouwing, kleine grids (8/16 combinaties), over-/undersamplingvergelijking, interne drempeltuning, metrics, zoektijd, plots en Raw-submissioncellen zijn toegevoegd. Kleine technische tests slagen; volledige modelscores, interpretatie en Kaggle-scores ontbreken nog. XGBoost 3.0.5 eenmalig installeren in de notebookomgeving. |
| 3.7 Eigen ensemble | Nog uit te werken | Een combinatie van minimaal drie modellen, motivatie, tuning, imbalance-vergelijking, resultaten en submission ontbreken. |
| Cross-validation, tuning en imbalance | Vijf modellen uitgevoerd, vergelijking incompleet | De opgeslagen uitvoer bevat tuningresultaten voor KNN, LR, SVM, Tree en RF. Scaling en resampling zitten binnen de trainingsfolds. Rapporteer per model ook de scores van minimaal twee imbalance-aanpakken; alleen de winnende sampler noemen is onvoldoende. Herstel de LR-regularisatievergelijking.                                                                                                  |
| Conclusie en advies                   | Niet gestart                                      | Modelvergelijking, beste-modelkeuze, bredere afwegingen en advies aan artsen ontbreken.                                                                                                                                                                                                                                                                                                                  |
| Codekwaliteit en reproduceerbaarheid  | Opgeslagen run gecontroleerd, eindcontrole nodig  | `toon_resultaten` en `maak_submission` zijn aanwezig. LR/SVM/Tree hebben nieuwe CSV's; KNN blijft Raw en RF mist nog een aanroep. Corrigeer de verouderde uitleg over Raw-cellen. Syntax en notebookstructuur zijn geldig; alle opgeslagen codecellen hebben uitvoer zonder errors, maar LR geeft regularisatiewaarschuwingen. Na inhoudelijke correcties blijft een volledige schone eindrun nodig. |
| Bronvermelding en AI-verantwoording   | Deels gereed                                      | Technische bronnen zijn toegevoegd; promptnummers, gedeelde links en de volledige APA- en AI-verantwoording zijn nog niet af.                                                                                                                                                                                                                                                                            |
| README                                | Later actualiseren                                | Werk na afronding de voortgang en uitvoerinstructies bij. Het README is met deze PvA-update niet aangepast.                                                                                                                                                                                                                                                                                              |

### Controle na de volledige run op 8 oktober

- KNN-afstandsformules en het rekenvoorbeeld zijn toegevoegd. Het SVM-voorbeeld gebruikt drie echte datasetrijen; scores en hinge loss zijn nagerekend.
- De eerder uitgevoerde kleine functietests waren technische tests. Nu bevat het notebook ook opgeslagen resultaten van de volledige modelgrids voor KNN, LR, SVM, Tree en RF.
- Notebookstructuur en Python-syntax zijn gecontroleerd. De metrics van de baseline en vijf modellen zijn opnieuw berekend uit de weergegeven confusion matrices en komen overeen met de opgeslagen metrics. De matrices en drempelplots zijn visueel gecontroleerd.
- Alle 11 aanwezige submissions bevatten 8.388 voorspellingen, de kolommen `id` en `stroke`, binaire labels, geen ontbrekende waarden en de juiste id-volgorde. Dit bewijst het formaat, niet een nieuwe Kaggle-score.
- Bij deze review zijn geen trainingen opnieuw gestart, geen notebookcellen of CSV's gewijzigd en geen bestanden op Kaggle ingediend. De controle gebruikt de opgeslagen run en bestanden; een onafhankelijke volledige herhaling is niet uitgevoerd.
- Nog open: LR herstellen, KNN- en RF-submission maken, ontbrekende modellen en conclusie uitwerken, bronnen aanvullen en de onderlinge review afronden.

### Aanvulling GBDT en XGBoost op 8 oktober

- Beide secties behouden hun bestaande kopjes en gebruiken dezelfde pipeline, splitsing, 5-fold CV-F1, interne 3-fold drempeltuning en gedeelde resultaat-/submissionfuncties als de andere modellen.
- GBDT vergelijkt 8 combinaties; XGBoost 16. Beide vergelijken over- en undersampling en twee combinaties van bomen/learning rate. XGBoost vergelijkt daarnaast L2-regularisatie. De code rapporteert ook de beste CV-variant per samplingtechniek en de totale zoektijd.
- De kleine technische test gebruikte 1.200 echte trainingsrijen, 1.000 validatierijen, 15 bomen en een beperkte grid. Training, resultaatfuncties, drempelplots, confusion matrices en CSV-formaat zijn getest; de vier testplots zijn visueel gecontroleerd.
- XGBoost 3.0.5 is voor de test in een losse map geïnstalleerd, niet in de bestaande notebookomgeving. De sectie bevat een installatie-instructie. Het notebookformaat en de syntax zijn gecontroleerd; eerdere modelcellen en hun uitvoer blijven behouden.
- De kleine testcijfers staan niet als definitieve modelresultaten in het notebook of deze tabel. Er zijn geen nieuwe Kaggle-submissions in het project gemaakt of ingediend.
- Nog te doen: volledige runs, resultaatinterpretatie, review en Kaggle-scores. Nieuwe bestanden worden pas door de notebookaanroepen gemaakt: `submission_gbdt_threshold_fixed_nieuw.csv` en `submission_xgb_threshold_fixed_nieuw.csv`.
- Technische bronnen zijn toegevoegd. De echte AI-modelgegevens, promptnummer en gedeelde chatlink moeten nog worden ingevuld.

### Actuele lokale resultaten

De validatieset bevat 6.710 rijen: 6.607 zonder stroke en 103 met stroke. CV-F1 is de gemiddelde score uit de modelselectie; validatiemetrics komen uit de aparte holdout. De F1-curve bij de drempelzoektocht gebruikt interne CV en hoeft dus niet dezelfde score te geven als deze tabel.

| Model                                | CV-F1            | Validatie-F1     | Precision | Recall | Accuracy | Beslisdrempel |
| ------------------------------------ | ---------------- | ---------------- | --------- | ------ | -------- | ------------- |
| LR-baseline                          | Niet getuned     | 0,0930           | 0,0493    | 0,8252 | 0,7531   | 0,5           |
| KNN                                  | 0,1257           | 0,1240           | 0,0781    | 0,3010 | 0,9347   | 0,808081      |
| Logistic Regression (huidige L2-run) | 0,1468           | **0,1497** | 0,0917    | 0,4078 | 0,9289   | 0,822144      |
| SVM                                  | **0,1567** | 0,1319           | 0,0803    | 0,3689 | 0,9255   | 1,125456      |
| Decision Tree                        | 0,1520           | 0,0971           | 0,0728    | 0,1456 | 0,9584   | 0,858586      |
| Random Forest                        | 0,1434           | 0,1109           | 0,0659    | 0,3495 | 0,9140   | 0,730032      |

- **KNN:** undersampling, 21 buren, Manhattan-afstand (`p=1`), afstandsweging.
- **LR:** undersampling, `C=100`, solver SAGA. De uitvoer noemt `l1_ratio=0`, maar alle ratio's gebruikten feitelijk L2. De score blijft een resultaat van deze L2-run; een eerlijke L1/L2-vergelijking ontbreekt. Gebruik bijvoorbeeld expliciet `penalty='elasticnet'` met de bestaande ratio's 0 en 1, of tune rechtstreeks `penalty=['l1', 'l2']` zonder `l1_ratio`. Zie [scikit-learn 1.6: LogisticRegression](https://scikit-learn.org/1.6/modules/generated/sklearn.linear_model.LogisticRegression.html).
- **SVM:** oversampling, lineaire kernel, `C=1`. De drempel geldt voor `decision_function`, niet voor een kans; een waarde boven 1 is daarom geldig.
- **Tree:** oversampling, Gini, `max_depth=5`, `min_samples_leaf=1`, `ccp_alpha=0`.
- **RF:** geen resampling in de winnende pipeline (`passthrough`), `class_weight='balanced_subsample'`, 300 bomen, `max_depth=5`, `max_features=0.5`, `min_samples_leaf=1`.
- LR heeft momenteel de hoogste validatie-F1; SVM de hoogste CV-F1. De historische Kaggle-score van KNN is dus niet hetzelfde als een overwinning op iedere lokale vergelijking.
- De featureselectie vóór de split is nog een methodologisch aandachtspunt. De lokale resultaten moeten daarom met die beperking worden besproken, niet als volledig onafhankelijke eindvalidatie.

### Nieuwe submissions uit deze run

| Bestand in de projectroot                     | Status en vergelijking met de eerdere submission                                                                                                                                                           |
| --------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `submission_lr_threshold_fixed_nieuw.csv`   | Aanwezig, 508 positieve voorspellingen; 168 labels verschillen van`submission_file/submission_lr_1.csv`. Na de regularisatiecorrectie opnieuw maken.                                                     |
| `submission_svm_threshold_fixed_nieuw.csv`  | Aanwezig, 624 positieve voorspellingen; één label verschilt van`submission_file/submission_svm_1.csv`. Een grote Kaggle-verbetering is daardoor niet waarschijnlijk.                                   |
| `submission_tree_threshold_fixed_nieuw.csv` | Aanwezig, 327 positieve voorspellingen; identiek aan`submission_file/submission_tree_1.csv`. Bij dezelfde evaluatie verwachten we dezelfde score; opnieuw uploaden levert geen andere voorspellingen op. |
| Nieuwe KNN-submission                         | Ontbreekt: de submissioncel is nog Raw. Het historische bestand blijft beschikbaar in`submission_file/`.                                                                                                 |
| RF-submission                                 | Ontbreekt: voeg een aanroep van de gedeelde submissionfunctie toe.                                                                                                                                         |

Nieuwe Kaggle-scores zijn nog niet aangeleverd. Koppel de oude scores hieronder niet automatisch aan gewijzigde bestanden. De drie nieuwe bestanden zijn nu gecontroleerd op formaat, niet op een nieuwe public score.

### Vastgelegde Kaggle-resultaten

Dit zijn de public scores uit de aangeleverde Kaggle-resultaten, geen nieuwe metingen. De minimumscore geldt voor minimaal één eigen teammodel, niet voor ieder model afzonderlijk.

| Submission                 | Public F1         |
| -------------------------- | ----------------- |
| KNN, eerste versie         | 0,09785           |
| KNN, eerdere drempelversie | 0,04968           |
| KNN, vaste gekozen drempel | **0,13071** |
| Logistic Regression        | 0,09352           |
| SVM                        | 0,09497           |
| Decision Tree              | 0,07272           |

KNN voldoet al aan de minimumscore. Voor de andere modellen blijft een volledige, eerlijke uitwerking vereist. Een hogere public score is geen bewijs dat een model geschikt is voor medische inzet.

## Werkverdeling

De eigenaar schrijft en test het onderdeel. De reviewer controleert de inhoud, code, bronnen en reproduceerbaarheid en moet het onderdeel daarna zelf kunnen uitleggen. Een onderdeel is pas klaar nadat de reviewer akkoord is.

| Onderdeel                                  | Eigenaar              | Reviewer          | Concrete verantwoordelijkheid                                                                                                                                                                            |
| ------------------------------------------ | --------------------- | ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Notebookstructuur en technische integratie | Tijn                  | Yorrick           | Nummering en volgorde bewaken, gedeelde imports/functies beheren en zorgen dat het notebook van boven naar beneden uitvoert.                                                                             |
| 1.1 t/m 1.8 Bestaande EDA                  | Tijn                  | Yorrick           | Maak de kolombeschrijvingen volledig, voeg targetgerichte analyses en datakwaliteitschecks toe en controleer de conclusies.                                                                              |
| 1.9 Belangrijkste Bevindingen              | Yorrick               | Tijn              | Bevindingen laten aansluiten op de getoonde analyses en onderscheid maken tussen correlatie en voorspellende waarde.                                                                                     |
| 1.10 Niet relevante kolommen               | Yorrick               | Tijn              | Valideer opschoningskeuzes; baseer featureverwijdering niet alleen op p-waarden; houd identifiers buiten de features.                                                                                    |
| 1.11 Standaardisatie                       | Tijn                  | Yorrick           | Theorie en basispipeline zijn toegevoegd; vul promptgegevens aan en gebruik de pipeline in latere schaalgevoelige modellen.                                                                              |
| 2 Evaluatie                                | Tijn                  | Yorrick           | Eerste uitwerking en baseline zijn aanwezig. Review 2.1–2.3, verwijder de placeholder in 2.1 en controleer de getoonde metrics en confusion matrix.                                                     |
| 3.1 Algemene modelaanpak                   | Tijn                  | Yorrick           | Tekst is klaar voor review. Controleer gedeelde pipeline, lekvrije CV/tuning-opzet en toepasbaarheid op alle modellen; Yorrick houdt het experiment- en Kaggle-log bij.                                  |
| 3.2 K-Nearest Neighbors                    | Tijn                  | Yorrick           | Training, metrics en matrix zijn aanwezig. Tijn voert de Raw-submissioncel uit; Yorrick reviewt theorie, instellingen en imbalance-vergelijking.                                                         |
| 3.3 Logistic Regression                    | Yorrick               | Tijn              | Herstel de genegeerde regularisatieparameter, herhaal alleen de benodigde LR-training/resultaten/submission en vergelijk L1/L2 en imbalance-aanpakken. Tijn controleert waarschuwingen en scoreherkomst. |
| 3.4 SVM                                    | Yorrick               | Tijn              | Training, matrix en CSV zijn aanwezig. Tijn corrigeert verouderde resultaattekst en rapporteert imbalance-vergelijking/Kaggle-score; Yorrick reviewt theorie, instellingen en scoreherkomst.             |
| 3.5 Decision Tree                          | Yorrick               | Tijn              | Bestaande uitwerking reviewen; gekozen pruning/parameters, lokale resultaten, imbalance-vergelijking en submission vastleggen.                                                                           |
| 3.6.1 Random Forest                        | Yorrick               | Tijn              | Training en metrics zijn aanwezig. Corrigeer kansmiddeling en scaling-uitleg, rapporteer imbalance-vergelijking en maak/dien de RF-submission in.                                                        |
| 3.6.2 Gradient Boosted Decision Trees      | Yorrick               | Tijn              | Boosting, sequentiële training, tuning, imbalance en Kaggle-submission.                                                                                                                                 |
| 3.6.3 XGBoost                              | Yorrick               | Tijn              | Boosting, trainingstijd, tuning, imbalance en Kaggle-submission.                                                                                                                                         |
| 3.7 Zelf samengesteld ensemble             | Tijn en Yorrick       | Onderlinge review | Tijn bouwt de technische combinatie; Yorrick motiveert modelkeuze en voting. Samen tuning, evaluatie en Kaggle-submission controleren.                                                                   |
| 4 Conclusie en advies                      | Yorrick, daarna Tijn  | Onderlinge review | Yorrick maakt de eerste vergelijking en conclusie. Tijn controleert scores, parameters en medische argumentatie. Samen bepalen zij het uiteindelijke advies.                                             |
| 5 Bronnen en AI-verantwoording             | Ieder voor eigen werk | Onderlinge review | Iedere auteur voegt bronnen direct toe. Tijn controleert promptverwijzingen bij code; Yorrick controleert de volledige APA-referentielijst en niet-AI-onderbouwing.                                      |
| Definitieve uitvoering en inlevering       | Tijn                  | Yorrick           | Tijn voert het notebook uit vanaf een schone kernel. Yorrick controleert de gerenderde inhoud, submissions en inleverbestanden.                                                                          |

### Samenwerkingsafspraken

1. Werk niet gelijktijdig in dezelfde notebookcellen. Spreek vooraf af welke sectie ieder op zijn eigen branch bewerkt.
2. De auteur levert per model ook de beste parameters, lokale metrics, confusion matrix, twee imbalance-vergelijkingen en Kaggle-score aan.
3. De reviewer controleert niet alleen taal, maar draait de cellen en legt de methode mondeling terug uit aan de auteur.
4. Bronnen en AI-prompts worden tijdens het schrijven toegevoegd, niet pas aan het einde.
5. Voeg pas samen als het onderdeel zelfstandig draait en geen resultaten uit latere notebookcellen nodig heeft.

### Omgaan met lange trainingsruns

- Tijdens het werken mogen dure trainingscellen Raw blijven. Zet alleen de benodigde trainingscellen tijdelijk terug naar Code wanneer je een model opnieuw wilt trainen.
- De vijf bestaande modelgrids zijn nu uitgevoerd. Herhaal ze niet alleen omdat een tekst of submissionaanroep verandert. Voor LR is hertraining wel nodig na herstel van de regularisatie. Wijzigingen aan features of de gezamenlijke validatieopzet vereisen opnieuw vergelijkbare resultaten voor alle betrokken modellen.
- Noteer na een run de pakketversies, random seeds, beste parameters, gekozen drempel, CV-score, validatiemetrics en submissionbestandsnaam. Opgeslagen uitvoer moet bij de huidige code horen.
- Voer eerst de imports, data/preprocessing, split en gedeelde functiecel onder 3.1 uit. Na een modeltraining toont `toon_resultaten` de actuele uitkomsten. Zet daarna de bijbehorende Raw-plot/matrix/submission naar Code en voer deze uit. De submissionfunctie traint opnieuw op alle ontwikkeldata, maar doet geen nieuwe drempelzoektocht.
- Bestaande Kaggle-scores blijven gekoppeld aan de oude bestanden. Geef een nieuwe submission pas een score na daadwerkelijk indienen; testuitvoer op een kleine dataset telt niet als definitief modelresultaat.
- Houd de grids klein en inhoudelijk onderbouwd. Geneste CV met drempeltuning vermenigvuldigt de rekentijd; start zware runs tijdig en voorkom onnodig tegelijk draaien op dezelfde computer.
- Voor de definitieve versie zijn benodigde trainings- en submissioncellen uitvoerbaar. Plan op 10 oktober één volledige run vanaf een schone kernel, inclusief de lange training. Een Run All die Raw-training overslaat bewijst niet dat het hele notebook reproduceerbaar is.
- Als die volledige run niet binnen de beschikbare tijd past, verklein de zoekruimte vóór de eindcontrole en rapporteer de opnieuw verkregen resultaten. Niet alleen oude uitvoer laten staan of verplichte modellen overslaan.

## Planning

| Uiterlijk gereed                            | Werkzaamheden                                                 | Klaar wanneer                                                                                                                                                                                                                                                                                  |
| ------------------------------------------- | ------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **8 oktober**                         | Concrete fouten herstellen en ontbrekende ensembles starten   | Tijn: KNN-submission uitvoeren, RF-submission toevoegen, verouderde SVM/Raw-uitleg corrigeren en EDA-reviewpunten oppakken. Yorrick: LR-regularisatie herstellen en LR opnieuw draaien; Tree-pruning toelichten en GBDT/XGBoost starten. Samen: pakketversies vastleggen en bronnen bijhouden. |
| **9 oktober, overdag**                | Ontbrekende modellen en vergelijkingen afronden               | GBDT/XGBoost hebben theorie, tuning, twee imbalance-aanpakken, parameters, CV-score, validatiemetrics, matrix en submission. Bestaande modellen krijgen een expliciete imbalance-vergelijking; gecorrigeerde LR-resultaten zijn opgeslagen.                                                    |
| **9 oktober, einde dag**              | Eigen ensemble en inhoudelijke conceptversie gereed           | Tijn bouwt het ensemble van minimaal drie modellen; Yorrick motiveert samenstelling/voting en begint de vergelijking/conclusie. Alle verplichte secties hebben inhoud, geen lege placeholders. Ontbrekende resultaten worden expliciet gemarkeerd en uiterlijk de volgende ochtend aangevuld.  |
| **10 oktober, ochtend**               | Resultaten, submissions, conclusie en bronnen compleet        | Eigenaren registreren de laatste Kaggle-resultaten. Yorrick maakt vergelijkingstabel, advies en APA-lijst af; Tijn controleert parameters, scoreherkomst, AI-verwijzingen en uitvoerbaarheid. README actualiseren. Geen nieuwe vrijblijvende score-experimenten meer.                          |
| **10 oktober, middag en avond**       | Volledige uitvoering, onderlinge review en definitieve versie | Tijn draait het volledige notebook vanaf een schone kernel met benodigde Code-cellen; Yorrick controleert inhoud en opdrachtchecklist. Beide begrijpen alle onderdelen. Na correcties horen code, uitvoer, tekst en submissions bij dezelfde versie.                                           |
| **11 oktober, ruim voor de deadline** | Inleveren en verifiëren                                      | Juiste notebookversie is ingeleverd, vereiste Kaggle-submission staat op naam van het team en de ontvangst/inleverstatus is gecontroleerd.                                                                                                                                                     |

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

1. **8 oktober — Tijn, review Yorrick:** review 3.1/3.2, voer de overgeslagen KNN-submissioncel uit en voeg een RF-submissionaanroep toe. De bestaande trainingen en matrices hoeven daarvoor niet opnieuw. Verwijder de placeholder in 2.1; de baseline-metrics zijn gecontroleerd.
2. **8–9 oktober — Yorrick, review Tijn:** herstel LR zodat L1/L2 werkelijk worden getuned. Herhaal de LR-gridsearch, resultaat-/plot-/matrixcellen en submission en controleer waarschuwingen. Bespreek voor Tree de gekozen pre-pruning en de daling van CV-F1 0,1520 naar validatie-F1 0,0971; dit is een signaal van beperkte generaliseerbaarheid, niet op zichzelf bewijs van overfitting.
3. **8–9 oktober — Tijn, review Yorrick:** SVM en RF zijn al getraind. Corrigeer de SVM-tekst die zegt dat resultaten ontbreken, de uitleg dat alle submissioncellen Raw zijn en de RF-uitleg over kansmiddeling. Maak per bestaand model een compacte vergelijking van de geteste imbalance-aanpakken uit `cv_results_`. Verduidelijk dat de SVM-drempel een beslissingsscore is.
4. **Uiterlijk 9 oktober — Yorrick, review Tijn:** GBDT en XGBoost zijn uitgewerkt. Installeer zo nodig XGBoost 3.0.5, voer beide volledige trainingen en resultaat-/plotcellen uit en bespreek de samplingvergelijking en fouttypen. Zet daarna hun submissioncellen van Raw naar Code, maak de bestanden en registreer de Kaggle-scores. **Tijn en Yorrick:** maak vervolgens het eigen ensemble met minimaal drie modellen, gemotiveerde voting, CV, tuning en twee imbalance-aanpakken.
5. **Uiterlijk 9 oktober — Tijn/Yorrick:** maak alle kolombeschrijvingen en targetgerichte EDA compleet. Toon noodzakelijke datakwaliteitschecks. Herzie te sterke conclusies over lage correlaties, woongebied en onbekende rookstatus; onbekend betekent niet automatisch nooit gerookt. Featurekeuzes mogen niet op de labels van de holdout worden afgestemd.
6. **Uiterlijk 10 oktober, ochtend — ieder eigen modellen, Yorrick overzicht:** leg per variant parameters, drempel, CV-instelling, imbalance-techniek, lokale metrics, submissionbestandsnaam en Kaggle-score/bewijs vast. Rond hoofdstuk 4, bronnen, AI-prompts en README af. Gebruik `sample_submission.csv` uitsluitend als formaatvoorbeeld.
7. **10 oktober — Tijn uitvoering, Yorrick review:** maak benodigde cellen uitvoerbaar en voer één volledige schone run uit. Controleer ook id-volgorde en 8.388 voorspellingen per submission, geen oude foutuitvoer, geen undefined variabelen en geen verschillen tussen gerapporteerde resultaten en code.
8. **Alleen als bovenstaande af is:** onderzoek betere scores met kleine, vooraf gekozen CV-experimenten. De huidige SVM-winnaar is al lineair met `C=1`; alleen opnieuw draaien verandert dat niet. Vergelijk op dezelfde CV-opzet en kies niet steeds op de public leaderboard. De minimumscore is al gehaald.

## Belangrijkste risico's

- **Omvang en tijd:** LR, SVM en Tree zijn toegevoegd, maar GBDT, XGBoost, het eigen ensemble, conclusie en bronverantwoording zijn nog niet compleet. Verplichte inhoud en gecontroleerde resultaten gaan vóór extra scoreverbetering.
- **Rekentijd:** uitgebreide grids met geneste drempeltuning kunnen uren duren. Raw-cellen voorkomen herhaald trainen tijdens het werken, maar vervangen geen definitieve uitvoering. Beperk zoekruimtes en start de eindrun tijdig.
- **LR-regularisatie:** de opgeslagen waarschuwingen bevestigen dat `l1_ratio` nu wordt genegeerd bij L2. De scores beschrijven een L2-model, maar onderbouwen geen L1/L2-vergelijking. Herstel dit vóór de eindrun en leg pakketversies vast (gecontroleerde omgeving: scikit-learn 1.6.1, imbalanced-learn 0.13.0, Python 3.13.5).
- **Datalekken:** resampling en standaardisatie moeten binnen de cross-validation-pipeline gebeuren, niet vooraf op de volledige trainingsdata.
- **Featureselectie op p-waarden:** de huidige woongebiedsectie verwijdert een feature omdat de chi-kwadraattoets niet significant is. Herzie dit besluit met voorspellende validatie; een niet-significante toets op associatie is op zichzelf geen bewijs dat een variabele de modelprestatie niet kan verbeteren.
- **Verouderde beschrijvingen:** de opgeslagen codecellen hebben nu een samenhangende uitvoervolgorde, maar de SVM-markdown, uitleg over Raw-cellen, README en EDA-todo lopen deels achter. Houd code, tekst, uitvoer en submissions bij dezelfde variant. De reviewer heeft de lange grids niet onafhankelijk opnieuw uitgevoerd.
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
