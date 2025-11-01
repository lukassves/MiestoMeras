# Miesto Meras

**Miesto Meras** – tai paprastas miesto valdymo simuliatorius sukurtas Java kalba.  
Žaidėjas tampa mero vaidmenyje ir turi priimti sprendimus, kurie lemia miesto biudžetą, gyventojų laimę, aplinką ir saugumą.

Projektas atliktas kaip **1-as ir 2-as namų darbai (ND1 + ND2)**.
 
---

## Žaidimo tikslas

Išlaikyti miestą stabilų ir laimingą kuo ilgiau, priimant teisingus sprendimus.

Žaidimas baigiasi, kai:  
- Miestas bankrutuoja (biudžetas ≤ 0)  
- Gyventojai tampa nelaimingi (laimė ≤ 0)  
- Arba pasiekiamas nustatytas turų skaičius (miestas išgyvena visą laiką)

---

## Kaip paleisti projektą

1. Atsisiųsk arba klonuok projektą:  
   [https://github.com/lukassves/MiestoMeras](https://github.com/lukassves/MiestoMeras)

2. Atidaryk projektą **IntelliJ IDEA** arba kitame Java IDE.

3. Paleisk failą:  
   `src/game/Main.java`

4. Pasirink sunkumo lygį:
   - **Normalus:** 10 turų, 30% atsitiktinių įvykių tikimybė  
   - **Sunkus:** 15 turų, 60% atsitiktinių įvykių tikimybė

---

## Žaidimo logika

Kiekviename ture žaidėjas gali:
- Statyti parką (+laimė, +aplinka, -biudžetas)
- Statyti policijos nuovadą (+saugumas, -biudžetas)
- Didinti mokesčius (+biudžetas, -laimė)
- Nieko nedaryti

Taip pat gali įvykti atsitiktiniai įvykiai:
- Gaisras miesto centre (nuostoliai biudžete)
- Protestas dėl mokesčių (mažėja laimė)
- Turizmo bumas (papildomos pajamos)

---

## Naudoti OOP principai

- **Encapsulation** – kiekvienas objektas saugo savo būseną (`City`, `Decision` ir kt.)  
- **Abstraction** – aiški klasių ir metodų struktūra  
- **Polymorphism** – įgyvendintas `GameStrategy` interfeisas  
- **Inheritance** – `GameMode.Normal` ir `GameMode.Hard` paveldi `GameStrategy`

---

## Naudoti dizaino pattern'ai

| Pattern | Kur naudotas | Paskirtis |
|----------|---------------|------------|
| Factory Method | `DecisionFactory` | Kuria sprendimus pagal žaidėjo pasirinkimą |
| Strategy | `GameMode` / `GameStrategy` | Leidžia keisti žaidimo sunkumo logiką |
| Observer (implicit) | `RandomEvent` | Simuliuoja atsitiktinius įvykius |

---


## Švaraus kodo principai

- Panaudotos **konstantos** (`GameConstants`) vietoje „magic numbers“  
- Klasės trumpesnės nei 200 eilučių, metodai – < 30 eilučių  
- Kodo struktūra aiški, logika padalinta į mažesnius vienetus  
- Nėra pasikartojančio kodo (DRY principas)

---


## Testavimas

Naudota **JUnit 5** (failas `CityTest.java'):

- `testApplyDecisionAffectsBudget()` – ar sprendimai keičia biudžetą  
- `testApplyDecisionAffectsHappiness()` – ar sprendimai keičia laimę  
- `testCityBankruptcyCondition()` – ar atpažįstamas bankrotas  
- `testRandomEventReducesBudget()` – ar įvykis keičia biudžetą  
- `testHardModeHasMoreEvents()` – ar „Hard“ režimas turi daugiau atsitiktinių įvykių


Visi testai praėjo sėkmingai.

Paleidimas:
`Right click on CityTest.java → Run 'CityTest'`

---

## Projekto struktūra
---
src/
└── game/
├── City.java
├── Decision.java
├── DecisionFactory.java
├── GameConstants.java
├── GameLoop.java
├── GameMode.java
├── GameStrategy.java
├── RandomEvent.java
├── SpecialEvent.java
├── CityTest.java
└── Main.java
---


## Autorius
Lukas Svešnikovas

---

## Statusas

- ND1 -done
- ND2 – done 
