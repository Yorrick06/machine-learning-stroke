De basis van de EDA staat, maar deze onderdelen ontbreken nog of moeten worden verdiept volgens de opdrachtomschrijving: :codex-file-citation{path="C:\Users\tijnd\Projects\machine-learning-stroke\opdracht_info\Opdracht_1_stroke_2026-27.docx" purpose="source"}.

## Noodzakelijke aanvullingen

1. **Kolombeschrijvingen completeren**
   - Iedere kolom afzonderlijk beschrijven.
   - `gender_Male`, `gender_Other` en alle dummyvariabelen expliciet behandelen.
   - Uitleggen wat het betekent wanneer bij een one-hotgroep alle kolommen `False` zijn, bijvoorbeeld mogelijk een onbekende rookstatus.
   - Eenheden vermelden bij leeftijd, glucose en BMI.

2. **Datakwaliteit uitgebreider controleren**
   - Dubbele rijen en dubbele `id`-waarden.
   - Oneindige waarden.
   - Onmogelijke of verdachte waarden en bereiken.
   - Controleren of one-hotgroepen geldig zijn.
   - Controleren of train en test dezelfde featurekolommen en datatypes hebben.

3. **Basisstatistieken voor iedere kolom**

   Momenteel zijn de uitgebreide statistieken vooral voor `age`, `avg_glucose_level` en `bmi` aanwezig. Voeg voor alle kolommen een compact overzicht toe met datatype, aantal unieke waarden, minimum, maximum, gemiddelde en/of klassefrequenties.

4. **Relaties met `stroke` beter onderzoeken**

   Alleen Pearson-correlaties zijn onvoldoende. Voeg bijvoorbeeld toe:
   - boxplots of verdelingsgrafieken van leeftijd, glucose en BMI uitgesplitst naar `stroke`;
   - strokepercentage per categorie voor hypertensie, hartziekte, geslacht, werk, burgerlijke staat, woonplaats en rookstatus;
   - aantallen én percentages, omdat de positieve klasse erg klein is.

5. **Uitschieters onderbouwen**

   De huidige conclusie dat uitschieters “waarschijnlijk realistische metingen” zijn, is nog niet bewezen. Kwantificeer de uitschieters en leg per variabele uit of ze plausibel zijn en waarom ze behouden, begrensd of verwijderd worden.

6. **Opschoning verder onderbouwen**
   - Controleren op dubbele of onbruikbare rijen.
   - Constante en bijna-constante kolommen beoordelen.
   - Redundante dummykolommen bespreken.
   - Zeldzame categorieën zoals `gender_Other` niet automatisch verwijderen; bespreek ook representativiteit en bias.
   - Iedere verwijdering motiveren.

7. **Standaardisatie uitwerken**
   - Betekenis en formule van standaardisatie uitleggen.
   - Benoemen dat KNN, Logistic Regression en SVM er doorgaans baat bij hebben.
   - Benoemen dat boommodellen het normaal gesproken niet nodig hebben.
   - Alleen binnen een pipeline en trainingsfold toepassen om datalekken te voorkomen.

8. **Belangrijkste bevindingen herzien**

   Werk Yorricks conclusies bij nadat bovenstaande analyses zijn toegevoegd. Vermijd uitspraken als “weinig voorspellende waarde” op basis van alleen een lage lineaire correlatie; een lage correlatie sluit niet-lineaire of gecombineerde voorspellende waarde niet uit.

## Sterk aanbevolen

- Vergelijk de featureverdelingen van train en test om mogelijke datasetverschuiving te herkennen.
- Voeg bronverwijzingen toe bij medische en statistische interpretaties.
- Maak herbruikbare functies voor herhaalde tabellen en visualisaties.
- Gebruik in grafieken altijd duidelijke titels, aslabels, legenda’s en aantallen.

De hoogste prioriteit ligt bij de target-relaties, volledige kolomstatistieken, datakwaliteitscontroles en standaardisatie. Daarmee voldoet de EDA inhoudelijk aan de opdracht; train-testvergelijking en uitgebreidere biasanalyse zijn waardevolle verdieping.

- EDA-aanvullingen uitvoeren
- Datakwaliteit controleren
- Targetrelaties visualiseren
