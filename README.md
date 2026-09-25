# Machine Learning Stroke

Portfolio-opdracht voor het voorspellen van herseninfarcten met verschillende classificatiemodellen. Inleverdatum: **11 oktober 2026**.

- `data/`: train-, test- en voorbeeldsubmissiondata
- `notebooks/index.ipynb`: EDA, modellering, evaluatie en conclusie
- `pva.md`: planning, taakverdeling en eisen

## Voortgang

- **EDA en voorbewerking:** grotendeels aanwezig; kolombeschrijvingen, extra controles en enkele keuzes over te verwijderen kenmerken moeten nog worden nagekeken.
- **Evaluatie (hoofdstuk 2):** train/validatiesplit, metrics, Logistic Regression-baseline en confusion matrix staan in het notebook; tekst en resultaten moeten nog worden gereviewd.
- **3.1 Algemene modelaanpak:** uitgewerkt; wacht op review door Yorrick.
- **3.2 K-Nearest Neighbors:** tuning, drempelonderzoek, confusion matrix en een Kaggle-submission zijn aanwezig; wacht op review door Yorrick. De afstandsuitleg en reproduceerbaarheid van de submissioncel zijn expliciete reviewpunten.
- **Kaggle:** beste eigen KNN-submission behaalde F1 **0,13071**. Daarmee is de minimumeis van 0,1 gehaald.
- **Nog te maken:** Logistic Regression als volledig model, SVM, Decision Tree, drie ensembles, een eigen ensemble, vergelijking, conclusie en advies. De baseline telt nog niet als volledige uitwerking van 3.3.

De actuele planning, werkverdeling en eisen per onderdeel staan in [pva.md](pva.md).
