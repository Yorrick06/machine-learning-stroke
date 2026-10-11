# Plan van aanpak portfolio-opdracht Stroke

## Doel en deadline

We leveren uiterlijk **zondag 11 oktober 2026 vóór 23:59** één net, genummerd Jupyter-notebook in. Het notebook bevat de EDA, voorbewerking, evaluatie, alle verplichte modellen en ensembles, cross-validation, hyperparametertuning, technieken voor klasse-onbalans, Kaggle-resultaten, conclusie en advies, en APA- en AI-bronvermeldingen.

De eerdere planning voor 8–10 oktober is vervangen door de actuele eindplanning hieronder. De modellen zijn inmiddels uitgevoerd. We richten ons nu op de laatste broncontrole, onderlinge review en het inleveren van de juiste versie, niet op extra score-experimenten.

## Huidige stand per 11 oktober 2026

De inhoudelijke hoofdstukken zijn aanwezig en alle verplichte modellen hebben opgeslagen resultaten. De oorspronkelijke targetgestuurde featureselectie is gecorrigeerd. Woongebied blijft behouden en alle huidige modellen gebruiken **16 features**. De modellen zijn daarna opnieuw uitgevoerd en de nieuwe submissions zijn volgens de aangeleverde Kaggle-resultaten ingediend.

**Random Forest heeft de hoogste actuele Kaggle Public F1: 0,13821.** Hiermee voldoet het team aan de minimumscore van 0,10. Niet ieder model hoeft afzonderlijk boven 0,10 te scoren.

Het project is inhoudelijk grotendeels klaar, maar nog niet automatisch definitief goedgekeurd. Vooral de volledige AI-verantwoording, de onderlinge review en de definitieve GitHub-/inleverstatus moeten nog worden bevestigd.

| Onderdeel | Status | Huidige stand en nog te doen |
|---|---|---|
| Mappen en data | Aanwezig | Train-, test- en voorbeeldsubmission staan in data/. Negen actuele features16-submissions staan in de projectroot; oudere bestanden blijven historisch. |
| Team- en Kaggle-informatie | Aanwezig; minimumscore gehaald | Teamnaam, teamleden en Kaggle-accounts staan in het notebook. Bewaar bewijs van de actuele score en controleer de team-/inleverstatus op Kaggle. |
| Kolombeschrijvingen en EDA | Uitgewerkt | Genderbeschrijvingen zijn aangevuld. De stroke_pct-tabel toont echte percentages. De uitschietertekst claimt niet meer dat waarden medisch betrouwbaar zijn; de ID-correlatie is aangepast naar ongeveer 0,0004. |
| Opschonen en standaardiseren | Gecorrigeerd en uitgevoerd | De split staat vóór de targetgerichte EDA. Referentiecategorieën worden alfabetisch gekozen, woongebied blijft behouden en alle rookstatuskolommen blijven staan. Scaling en sampling staan binnen de pipelines. |
| 2 Evaluatie | Uitgewerkt en uitgevoerd | Split, metricformules, baseline en confusion matrix zijn aanwezig. De eerdere placeholder is verwijderd. |
| 3.1 Algemene modelaanpak | Uitgewerkt; onderlinge review bevestigen | Gedeelde CV-, tuning-, imbalance- en drempelaanpak zijn beschreven. Resterende evaluatiebeperkingen worden benoemd. |
| 3.2 KNN | Uitgevoerd en gecontroleerd; onderlinge review bevestigen | Afstandsformules, rekenvoorbeeld, parameters, lokale metrics, confusion matrix en actuele submission zijn aanwezig. |
| 3.3 Logistic Regression | Gecorrigeerd en uitgevoerd | De eerdere genegeerde regularisatieparameter is hersteld. L1/L2 worden werkelijk vergeleken; de huidige winnaar gebruikt L1 met C=0,1. |
| 3.4 SVM | Uitgevoerd en uitgewerkt | Rekenvoorbeeld, tuning, metrics, matrix en submission zijn aanwezig. Support vectors, slackvoorwaarden en RBF-uitleg zijn verduidelijkt. |
| 3.5 Decision Tree | Uitgevoerd en uitgewerkt | Parameters, metrics, matrix en submission zijn aanwezig. Pre-/post-pruning en de geschaalde, deels getoonde boomplot worden toegelicht. |
| 3.6.1 Random Forest | Uitgevoerd; beste actuele Kaggle-model | Kansmiddeling is correct beschreven. De actuele submission en score zijn vastgelegd. |
| 3.6.2 GBDT en 3.6.3 XGBoost | Volledige runs aanwezig | Theorie, keuzes, grids, over-/undersampling, zoektijden, metrics, matrices en Kaggle-resultaten staan in het notebook. Geen ontbrekende modelruns meer. |
| 3.7 Eigen ensemble | Beide varianten uitgevoerd | KNN, LR en XGBoost worden gecombineerd. Gelijke gewichten [1,1,1] en getunede gewichten [2,2,1] hebben afzonderlijke evaluaties, matrices, submissions en Kaggle-scores. |
| 4 Conclusie en advies | Uitgewerkt en geactualiseerd | De vergelijking maakt onderscheid tussen CV, lokale validatie en Kaggle. RF is de Kaggle-winnaar; medische inzetbaarheid wordt niet geclaimd. |
| Codekwaliteit | Gecontroleerd | 60 codecellen, geen Raw-cellen, geldige syntax en notebookstructuur. De laatste automatische PEP8-controle vond geen overtredingen. |
| Reproduceerbaarheid | Instructies en afhankelijkheden aanwezig | README en requirements.txt beschrijven de uitvoering. Een onafhankelijke volledige schone run en installatie in een nieuwe omgeving zijn niet opnieuw uitgevoerd. |
| Bronnen en AI-verantwoording | Aanwezig; eindcontrole open | De recente PEP8-/README-verwijzingen noemen nu consistent GPT-6.1 Sol. De hoofdpromptlijst en losse AI-chats moeten nog volledig worden gecontroleerd op modelversie, datum, titel en promptverwijzingen. |
| GitHub en inlevering | Nog zelf bevestigen | Commit en push de eindversie. Zorg dat de juiste branch wordt ingeleverd en dat de standaardbranch past bij de README-cloneopdracht. Controleer de ontvangst vóór 23:59. |

### Actuele resultaten: 16 features

CV-F1 en validatieresultaten komen uit de opgeslagen notebookuitvoer. Kaggle Public F1 komt uit de door het team aangeleverde resultaten; deze scores zijn niet tijdens de laatste controle opnieuw op Kaggle gemeten.

De ontwikkelset bevat 26.840 rijen, waarvan 414 met stroke. De validatieset bevat 6.710 rijen: 6.607 zonder stroke en 103 met stroke.

| Model | CV-F1 | Validatie-F1 | Precision | Recall | Kaggle Public F1 |
|---|---:|---:|---:|---:|---:|
| KNN | 0,1237 | 0,1097 | 0,0676 | 0,2913 | 0,10876 |
| Logistic Regression | 0,1470 | 0,1072 | 0,0648 | 0,3107 | 0,10631 |
| SVM | 0,1478 | 0,1058 | 0,0742 | 0,1845 | 0,08474 |
| Decision Tree | **0,1510** | 0,0971 | 0,0728 | 0,1456 | 0,07272 |
| Random Forest | 0,1461 | 0,1328 | 0,0831 | 0,3301 | **0,13821** |
| GBDT | 0,1427 | 0,1268 | 0,0758 | 0,3883 | 0,08988 |
| XGBoost | 0,1468 | 0,1198 | 0,0712 | 0,3786 | 0,09545 |
| Soft Voting [1,1,1] | 0,1414 | **0,1382** | 0,0861 | 0,3495 | 0,12328 |
| Soft Voting [2,2,1] | 0,1448 | 0,1189 | 0,0761 | 0,2718 | 0,12927 |

- Decision Tree heeft de hoogste CV-F1, Soft Voting [1,1,1] de hoogste opgeslagen validatie-F1 en Random Forest de hoogste Kaggle Public F1.
- Het gewogen ensemble scoort lager op lokale validatie, maar hoger op Kaggle dan het gelijkgewogen ensemble. We hebben niet onderzocht waarom deze rangorde verschilt.
- CV-F1 is een selectiescore, geen onafhankelijke eindscore. De interne CV-score uit een drempelplot hoeft niet gelijk te zijn aan de validatie-F1.
- De LR-baseline blijft een afzonderlijk, niet-getuned experiment met validatie-F1 0,0930.

### Beste instellingen en beslisdrempels

| Model | Beste gevonden instellingen | Imbalance in de gekozen configuratie | Beslisdrempel |
|---|---|---|---:|
| KNN | 21 buren, Euclidisch (p=2), distance-gewichten | RandomUnderSampler | 0,797980 |
| Logistic Regression | L1, C=0,1, solver SAGA | RandomUnderSampler | 0,795655 |
| SVM | Lineaire kernel, C=0,1 | RandomOverSampler | 1,392398 |
| Decision Tree | Gini, max_depth=5, min_samples_leaf=1, ccp_alpha=0 | RandomOverSampler | 0,858586 |
| Random Forest | 300 bomen, max_depth=5, min_samples_leaf=10, max_features=sqrt, geen extra class weights | RandomUnderSampler | 0,758031 |
| GBDT | 100 bomen, learning_rate=0,1, max_depth=2, min_samples_leaf=5 | RandomOverSampler | 0,759348 |
| XGBoost | 100 bomen, learning_rate=0,1, max_depth=2, reg_lambda=1 | RandomOverSampler | 0,756843 |
| Soft Voting [1,1,1] | KNN, LR en XGBoost met gelijke gewichten | Sampling binnen de basispipelines en drempeltuning | 0,786840 |
| Soft Voting [2,2,1] | Dezelfde basismodellen, gewichten gekozen met GridSearchCV | Sampling binnen de basispipelines en drempeltuning | 0,797801 |

De SVM-drempel hoort bij decision_function en is geen kans. Een drempel boven 1 is daarom geldig. Voor de submissions wordt de gekozen drempel vastgehouden; maak_submission() traint de gekozen pipeline opnieuw op alle gelabelde data.

### Actuele submissions

| Bestand in de projectroot | Positieve voorspellingen | Kaggle Public F1 |
|---|---:|---:|
| submission_knn_threshold_fixed_nieuw_features16.csv | 540 | 0,10876 |
| submission_lr_threshold_fixed_nieuw_features16.csv | 513 | 0,10631 |
| submission_svm_threshold_fixed_nieuw_features16.csv | 364 | 0,08474 |
| submission_tree_1_features16.csv | 327 | 0,07272 |
| submission_rf_features16.csv | 382 | **0,13821** |
| submission_gbdt_features16.csv | 799 | 0,08988 |
| submission_xgb_features16.csv | 806 | 0,09545 |
| submission_soft_voting_gelijk1_features16.csv | 494 | 0,12328 |
| submission_soft_voting_gewogen_2_2_1_features16.csv | 420 | 0,12927 |

Alle negen actuele bestanden zijn bij de laatste controle gecontroleerd op 8.388 rijen, de kolommen id en stroke, binaire voorspellingen en de juiste ID-volgorde. Dit bewijst het formaat, niet onafhankelijk de Kaggle-score of de volledige herkomst van iedere voorspelling.

**Historisch:** de beste oude Kaggle-score was 0,13071 met KNN en 15 features. Die score hoort niet bij het huidige KNN-model. Oudere bestanden en experimenten blijven als geschiedenis beschikbaar. Uit gewijzigde scores trekken we geen causale conclusie over het toevoegen van woongebied.

### Wat de laatste controle wel en niet aantoont

- De vroege gestratificeerde split gebruikt test_size=0.2, random_state=42 en stratify=y. De feature-/indexcontroles en de bestaande kernel sluiten aan op de opgeslagen resultaten.
- Alle negen huidige modelconfiguraties in de bestaande kernel gebruiken 16 features; de drempels en CV-scores komen overeen met het notebook.
- De recente PEP8-opmaak veranderde de uitvoerbare codestructuur en opgeslagen modeluitvoer niet. Er zijn geen opgeslagen error-uitvoerblokken; de KNN-uitvoer bevat wel een joblib-waarschuwing over CPU-detectie, waarna resultaten zijn berekend.
- De lokaal vastgelegde requirements passen bij de geïnstalleerde versies en pip check slaagde. De omgeving gebruikt onder andere Python 3.13.5, scikit-learn 1.6.1, imbalanced-learn 0.13.0 en XGBoost 3.4.1.
- De lange modeltrainingen zijn bij de laatste kwaliteitscontrole niet opnieuw uitgevoerd. Er is ook geen nieuwe installatie in een schone omgeving getest. De laatste tekstcorrecties vormen op zichzelf geen reden om opnieuw te trainen.
- De actuele GitHub-serverstatus kon door een verbindingsfout niet worden gecontroleerd. Gedeelde AI-chats en Kaggle-scores zijn niet onafhankelijk online geverifieerd.
- Dit PvA legt verantwoordelijkheden vast, maar is geen bewijs dat Tijn en Yorrick ieder onderdeel al persoonlijk hebben goedgekeurd.

## Werkverdeling

De oorspronkelijke eigenaren blijven gelijk. De technische controle is gedaan, maar de teamleden bevestigen zelf hun onderlinge review. Schrijf pas dat een onderdeel definitief is afgerond als de reviewer akkoord is en beide teamleden het kunnen uitleggen.

| Onderdeel | Eigenaar | Reviewer | Laatste verantwoordelijkheid |
|---|---|---|---|
| Notebookstructuur en integratie | Tijn | Yorrick | Eindversie, celvolgorde, gedeelde functies en juiste GitHub-branch controleren. |
| 1.1 t/m 1.8 EDA | Tijn | Yorrick | Kolombeschrijvingen, percentages, figuren en datakwaliteitsconclusies nalopen. |
| 1.9 Belangrijkste Bevindingen | Yorrick | Tijn | Bevindingen laten aansluiten op ontwikkeldata; geen causale of medische claims zonder onderbouwing. |
| 1.10 Niet relevante kolommen | Yorrick | Tijn | ID, alfabetische referentiecategorieën, behouden woongebied en rookstatus kunnen uitleggen. |
| 1.11 Standaardisatie | Tijn | Yorrick | Schaalpipeline en toepassing binnen CV uitleggen. |
| 2 Evaluatie | Tijn | Yorrick | Metricformules, baseline, split en confusion matrix nalopen. |
| 3.1 Algemene modelaanpak | Tijn | Yorrick | CV, tuning, sampling, drempels en beperkingen controleren. |
| 3.2 KNN | Tijn | Yorrick | Afstanden, voorbeeld, huidige p=2, resultaten en submission controleren. |
| 3.3 Logistic Regression | Yorrick | Tijn | Loss, gradient descent, L1/L2 en huidige instellingen controleren. |
| 3.4 SVM | Yorrick | Tijn | Margin, kernels, rekenvoorbeeld en beslissingsscore uitleggen. |
| 3.5 Decision Tree | Yorrick | Tijn | Splitscriteria, pruning en boomplot controleren. |
| 3.6.1 Random Forest | Yorrick | Tijn | Kansmiddeling, parameters en score van de huidige Kaggle-winnaar controleren. |
| 3.6.2 GBDT en 3.6.3 XGBoost | Yorrick | Tijn | Boosting, parallel/sequentieel, samplingvergelijking en resultaten controleren. |
| 3.7 Eigen ensemble | Tijn en Yorrick | Onderlinge review | Gelijke/getunede gewichten, aparte drempels, matrices en submissions gescheiden houden. |
| 4 Conclusie en advies | Yorrick, daarna Tijn | Onderlinge review | Scores, RF-keuze, evaluatiebeperkingen en voorzichtig medisch advies controleren. |
| 5 Bronnen en AI-verantwoording | Ieder voor eigen werk | Onderlinge review | Tijn controleert prompts/comments; Yorrick controleert APA en niet-AI-onderbouwing. Samen ontbrekende metadata en gedeelde links nalopen. |
| Definitieve inlevering | Tijn | Yorrick | Commit/push, juiste branch, juiste notebookbestand en ontvangst vóór 23:59 bevestigen. |

### Samenwerkingsafspraken en lange runs

1. Werk niet gelijktijdig in dezelfde notebookcellen. Spreek af wie de eindversie bewaart.
2. Beide teamleden moeten alle tekst en code kunnen uitleggen, niet alleen hun eigen onderdeel.
3. Herhaal geen grids alleen omdat Markdown of dit PvA verandert. Een eventuele nieuwe feature-, model- of splitwijziging vraagt wel om controle van de gevolgen voor resultaten en submissions.
4. In de huidige eindversie staan geen Raw-cellen. Een volledige Run All kan uren duren en submissioncellen overschrijven bestaande CSV's. Start dit niet onnodig vlak vóór de deadline.
5. Volg voor lokaal uitvoeren de README en requirements.txt. De XGBoost-comment met 3.0.5 is verouderd; gebruik de vastgelegde omgeving met 3.4.1. Dit bewijst niet welke versie bij iedere historische run is gebruikt.
6. Bewaar bestaande resultaten. Geef een nieuw bestand pas een Kaggle-score na daadwerkelijk indienen.
7. De onafhankelijke schone eindrun is niet opnieuw aangetoond. Presenteer de technische controle dus niet als een volledige reproductie.

## Planning voor 11 oktober

| Volgorde | Werk | Verantwoordelijk | Klaar wanneer |
|---|---|---|---|
| Eerst, vóór de laatste commit | AI-verantwoording afmaken | Ieder eigen gebruik; Tijn prompts, Yorrick APA | Metadata, promptverwijzingen en gedeelde links zijn gecontroleerd; overnamegrenzen zijn nagegaan. |
| Daarna | Korte onderlinge eindcontrole | Tijn en Yorrick | Beide begrijpen theorie/code, zien correcte figuren en bevestigen de juiste scores en modelconfiguraties. |
| Daarna, met tijd voor herstel | Eindversie publiceren | Tijn, controle Yorrick | Laatste wijzigingen zijn gecommit/gepusht; juiste branch staat online en de README verwijst naar de uitvoerbare versie. |
| Uiterlijk 11 oktober vóór 23:59 | Inleveren en ontvangst controleren | Tijn, controle Yorrick | Het juiste notebook is ingeleverd, de ontvangst is bevestigd en Kaggle-bewijs is beschikbaar. |

Wacht niet tot de laatste minuten. Nieuwe modellen, grotere grids en extra leaderboard-experimenten zijn geen onderdeel meer van deze eindplanning.

## Eisen per onderdeel

### Algemene eisen aan het notebook

- Er wordt precies één net en duidelijk gestructureerd notebook ingeleverd.
- Hoofdstukken en paragrafen zijn genummerd; tekst staat in markdowncellen en uitvoerbare code in codecellen.
- Herhaalde logica staat zo veel mogelijk in zelfgedefinieerde functies. OOP heeft volgens de opdracht de voorkeur, maar is geen harde eis.
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

- Eén overzichtstabel bevat de notebookscores en Kaggle-scores van alle modellen en ensembles. De beste parameters staan bij de betreffende modellen.
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

### Nog afronden vóór inleveren

1. **Tijn en Yorrick — hoofdstuk 5:** controleer en vul ontbrekende promptnummers, gebruiksdatums, modelversies en chattitels aan bij de hoofdlijst en losse Claude-/ChatGPT-chats. Neem recente featureselectie- en ensembleondersteuning mee. Een PEP8-comment verantwoordt niet automatisch de oorspronkelijke AI-code.
2. **Ieder eigen gebruik:** controleer gedeelde links en de opdrachtgrenzen van maximaal 5% letterlijk overgenomen tekst en 25% letterlijk overgenomen code. De laatste controle heeft de oorspronkelijke chats/bronnen niet volledig vergeleken en bewijst deze percentages niet.
3. **Tijn en Yorrick:** bevestig de onderlinge review. De formulering in hoofdstuk 5 dat alles door een teamlid is gecontroleerd moet overeenkomen met wat jullie werkelijk hebben nagekeken.
4. **Tijn, controle Yorrick:** commit en push de definitieve versie. Merge zo nodig naar de standaardbranch, of geef duidelijk aan welke branch de docent moet gebruiken. Controleer dit zelf op GitHub.
5. **Tijn, controle Yorrick:** lever het juiste notebook vóór 23:59 in en controleer de ontvangst en het Kaggle-bewijs.

### Kleine verbeterpunten, niet nodig voor nieuwe training

- **Notebookcel 70, historisch leeftijdsgewichtexperiment:** de uitspraak dat validatie-F1 licht verbeterde heeft daar geen getoonde waarden. Voeg oorspronkelijke waarden toe als ze beschikbaar zijn, of schrap de uitspraak.
- **Notebookcel 105:** maak eventueel de oude XGBoost-installatiecomment consistent met requirements.txt. De README waarschuwt hiervoor al; verander nu niet onnodig de omgeving.
- Controleer de gerenderde figuren en formules nog eenmaal. Een HTML-export zonder uitvoering kan helpen, maar is geen expliciete eis in de gelezen opdracht.
- Extra nested CV, calibratie, fairnessonderzoek en grotere grids kunnen later. Ze zijn geen reden om nu de bestaande resultaten te vervangen.

**Al gecorrigeerd in het huidige notebook:** de RBF-uitleg, de te sterke uitschieterclaim, de ID-correlatie en de tegenstrijdige modelnamen bij de recente PEP8-/README-AI-verwijzingen. Deze punten staan niet meer als open actie.

## Belangrijkste resterende risico's

- **Bronnen en AI:** onvolledige AI-verwijzingen en niet-gecontroleerde overnamepercentages blijven een formeel risico. Vul alleen echte gegevens in; verzin geen datums of modelversies.
- **Eindversie:** lokale wijzigingen zijn niet automatisch online of ingeleverd. De actuele GitHub-/inleverstatus moet het team zelf bevestigen.
- **Evaluatie:** de validatieset is eerder bekeken. De beste CV-scores zijn gebruikt voor selectie; bij het eigen ensemble zijn basisinstellingen vooraf op alle ontwikkeldata gekozen. De ensemble-CV is daardoor geen volledig onafhankelijke evaluatie van het hele selectieproces.
- **Reproduceerbaarheid en rekentijd:** de opgeslagen resultaten en technische controles zijn beschikbaar, maar een volledige onafhankelijke schone run/installatie is niet opnieuw bewezen. Een onnodige Run All vlak vóór de deadline kan uren kosten en CSV's overschrijven.
- **Medische interpretatie:** de lage precision en recall maken de modellen niet geschikt voor zelfstandige medische beslissingen. RF is een kandidaat voor verder onderzoek, niet een bewezen veilig klinisch systeem.
- **Historische scores:** koppel de oude KNN-score van 0,13071 niet aan het huidige model met 16 features. Veranderingen bewijzen niet dat woongebied de oorzaak is.

## Definitie van klaar

De opdracht is klaar wanneer de juiste nette, genummerde notebook is ingeleverd, alle verplichte onderdelen en resultaten bevat, met de beschreven omgeving uitvoerbaar is, een eigen Kaggle-score van minimaal 0,10 aantoont, correcte bron- en AI-verantwoording bevat en door beide teamleden kan worden uitgelegd.

Op dit moment zijn de inhoud en actuele scores aanwezig. De open bron-/review-/inlevercontroles hierboven moeten nog worden bevestigd. Dit PvA zet die punten niet zonder bewijs op afgerond.

## Controle van dit plan tegen de opdrachtomschrijving

Dit plan dekt de expliciete onderdelen van Opdracht_1_stroke_2026-27.docx: notebookstructuur, PEP8, EDA, voorbewerking, metrics en berekeningen, alle verplichte modellen met theorie, CV/tuning en imbalance-technieken, Kaggle-submissions, vergelijking, conclusie, advies en APA-/AI-verantwoording.

De minimumeis is minstens één eigen teammodel met F1 van minimaal 0,10; niet ieder model hoeft deze grens te halen. OOP heeft de voorkeur, maar is geen harde eis. Een HTML-export is in de gelezen opdracht niet verplicht.

De toetsmatrijs in opdracht_info noemt collegejaar 2024–2025 en wordt alleen aanvullend gebruikt. De opdrachtomschrijving 2026–2027 is leidend; de volledige actuele gedetailleerde rubric is hiermee niet onafhankelijk geverifieerd.

Deze actualisatie wijzigt alleen pva.md. Notebookcode, teksten, opgeslagen uitvoer, instellingen, README, requirements en submissionbestanden worden hierbij niet aangepast. Er worden geen trainingen uitgevoerd.
