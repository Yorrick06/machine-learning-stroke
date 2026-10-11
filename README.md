# Machine Learning Stroke

Portfolio-opdracht van Tijn Duivenvoorden en Yorrick de Vries voor het voorspellen van herseninfarcten. Het notebook bevat de EDA, voorbewerking, evaluatie, KNN, Logistic Regression, SVM, Decision Tree, Random Forest, GBDT, XGBoost, een Soft Voting-ensemble en de conclusie. Inleverdatum: **11 oktober 2026**.

## Projectbestanden en datasets

```text
machine-learning-stroke/
├── README.md
├── requirements.txt
├── data/
│   ├── train.csv              # 33.550 rijen, inclusief target stroke
│   ├── test.csv               # 8.388 rijen, zonder target
│   └── sample_submission.csv  # Voorbeeldformaat: id,stroke
├── notebooks/
│   └── index.ipynb            # Volledige uitwerking
├── submission_file/           # Historische submissions
└── pva.md                     # Planning en werkverdeling
```

De drie datasets staan al in de Git-repository. Bij een volledige clone is geen aparte download nodig. Houd de bestandsnamen en mapstructuur aan: het notebook leest `../data/train.csv`, `../data/test.csv` en `../data/sample_submission.csv` vanuit de map `notebooks`. De actuele submissionbestanden staan in de projectroot en hebben `features16` in de naam.

## Installeren en uitvoeren

Gebruik **Python 3.13.5**, dezelfde versie als in de lokale omgeving en de notebookmetadata. Download de repository via GitHub als ZIP en pak deze uit, of clone hem:

```bash
git clone https://github.com/Yorrick06/machine-learning-stroke.git
cd machine-learning-stroke
```

Maak vanuit de projectroot een virtuele omgeving:

```bash
python -m venv .venv
```

Activeer deze in Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

Op macOS/Linux:

```bash
source .venv/bin/activate
```

Installeer de dependencies, registreer de kernel en start JupyterLab **vanuit `notebooks`**:

```bash
python -m pip install -r requirements.txt
python -m ipykernel install --user --name machine-learning-stroke --display-name "Python (machine-learning-stroke)"
cd notebooks
python -m jupyterlab index.ipynb
```

Selecteer in JupyterLab de kernel **Python (machine-learning-stroke)** en kies **Kernel → Restart Kernel and Run All Cells**. Voer het notebook van boven naar beneden uit: latere model- en ensemblecellen gebruiken variabelen uit eerdere cellen. De volledige cross-validation, gridsearch en drempeltuning kunnen uren duren en gebruiken via `n_jobs=-1` meerdere CPU-kernen. De submissioncellen trainen opnieuw op alle gelabelde data en schrijven CSV's in de projectroot; bestaande bestanden met dezelfde naam worden overschreven. Er is geen Kaggle-account nodig voor de lokale uitvoering; indienen op Kaggle gebeurt afzonderlijk.

## Dependencies en controle

[requirements.txt](requirements.txt) legt de daadwerkelijk geïnstalleerde versies op 11 oktober 2026 vast voor alle externe notebookimports, JupyterLab en de Python-kernel. Standaardbibliotheekmodule `time` vereist geen installatie. Het bestand bevat de directe dependencies; indirecte dependencies worden door pip geïnstalleerd en zijn niet afzonderlijk vastgezet.

XGBoost is lokaal **3.4.1**. Een bestaande installatiecomment in het notebook noemt **3.0.5**; gebruik voor deze installatie het requirementsbestand. De huidige lokale versie bewijst niet welke versie bij iedere eerder opgeslagen modelrun is gebruikt.

Bij deze documentatie-update zijn de imports, datasetpaden, lokale pakketversies en pakketconsistentie gecontroleerd. Er is geen nieuwe volledige notebookrun of installatie in een schone omgeving uitgevoerd. De opgeslagen resultaten zijn dus niet onafhankelijk opnieuw gereproduceerd. De AI-verantwoording voor deze update staat in hoofdstuk 5 van het notebook.
