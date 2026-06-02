# Návod ke spuštění

## Požadavky

- Python 3.12 nebo novější
- Jupyter Notebook nebo JupyterLab
- Knihovny: `numpy`, `pandas`, `openpyxl`, `PuLP`

## Instalace a spuštění

1. Stáhněte repozitář:
   - **ZIP:** tlačítko **Code → Download ZIP**, rozbalte složku `DP_SULTA_JAN_PRILOHY-main`
   - **Git:** `git clone https://github.com/jansulta/DP_SULTA_JAN_PRILOHY.git`

2. Nainstalujte potřebné knihovny:

```bash
pip install numpy pandas openpyxl pulp
```

3. Spusťte Jupyter z adresáře se staženými soubory:

```bash
cd DP_SULTA_JAN_PRILOHY
jupyter notebook
```

4. Otevřete libovolný notebook. Dataset `small_dataset.xlsx` se načte automaticky. Pokud jsou notebook a dataset ve stejném adresáři, není třeba nic upravovat.

## Obsah repozitáře

| Soubor | Popis |
|--------|-------|
| `small_dataset.xlsx` | Syntetická instance, 30 uzlů (29 zákazníků + 1 depot) |
| `DP_SULTA_JAN_MILP.ipynb` | Referenční MILP model (solver PuLP/CBC) |
| `DP_SULTA_JAN_HS.ipynb` | Metoda Harmony Search |
| `DP_SULTA_JAN_ACO.ipynb` | Metoda Ant Colony Optimization |
| `DP_SULTA_JAN_BS.ipynb` | Metoda Beam Search |

Každý notebook je samostatný a lze ho spustit nezávisle na ostatních. Doporučené pořadí: MILP → HS → ACO → BS.

## Konfigurovatelné parametry

Každý notebook obsahuje v úvodních buňkách konfigurační třídu. Níže je přehled parametrů, které může uživatel měnit.

### MILP

**Buňka 2**, sekce *1. Konfigurace parametrů instance*, třída `Config`

| Parametr | Výchozí | Popis |
|----------|---------|-------|
| `m` | 3 | Počet vozidel |
| `Q` | 13 | Kapacita vozidla |
| `pi` | 1.5 | Penalizační koeficient za zpoždění (γ) |
| `Pskip` | 18.0 | Penalizace za neobsloužení zákazníka |
| `time_limit_sec` | 1800 | Časový limit solveru v sekundách |
| `gapRel` | 0.10 | Toleranční gap pro předčasné ukončení |

### Harmony Search

Parametry instance: **buňka 1**, úvodní buňka s importy, třída `Config` (shodná s MILP).

Parametry algoritmu: **buňka 11**, sekce *10. Spuštění experimentu*, volání `harmony_search(...)`

| Parametr | Výchozí | Popis |
|----------|---------|-------|
| `HMS` | 20 | Velikost Harmony Memory |
| `NI` | 1000 | Počet iterací |
| `HMCR` | 0.90 | Pravděpodobnost využití paměti |
| `PAR` | 0.20 | Pravděpodobnost operátoru pitch adjustment |

### Ant Colony Optimization

Parametry instance: **buňka 1**, úvodní buňka s importy, třída `Config` (shodná s MILP).

Parametry algoritmu: **buňka 4**, sekce *3. Parametry ACO a inicializace feromonové matice*, třída `ACOParams`

| Parametr | Výchozí | Popis |
|----------|---------|-------|
| `N_ANTS` | 50 | Počet mravenců v kolonii |
| `N_ITER` | 1000 | Počet iterací |
| `ALPHA` | 1.0 | Váha feromonové složky |
| `BETA` | 2.0 | Váha heuristické složky |
| `RHO` | 0.20 | Rychlost odpařování feromonů |
| `ELITIST` | True | Aktualizace feromonů nejlepším řešením |

### Beam Search

Parametry instance: **buňka 1**, úvodní buňka s importy, třída `Config` (shodná s MILP).

Parametry algoritmu: **buňka 4**, sekce *3. Parametry Beam Search*, třída `BeamParams`

| Parametr | Výchozí | Popis |
|----------|---------|-------|
| `OMEGA` | 30 | Šířka svazku (beam width) |

## Reprodukovatelnost

Stochastické metody (HS, ACO) používají `SEED = 42`. Metoda BS je deterministická. Generování časových oken je shodné ve všech noteboocích.
