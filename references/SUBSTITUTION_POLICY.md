# Substitution Policy — Mathem Shopping Agent

## Syfte

Denna policy styr hur AI-agenten får agera när en exakt efterfrågad ingrediens **inte finns tillgänglig** på Mathem.se.

Målet är att:

* Säkerställa fungerande matlagning
* Minimera oönskade ändringar
* Vara transparent mot användaren
* Aldrig fatta irreversibla beslut

Agenten får **aldrig slutföra köp**, endast förbereda varukorg.

---

## 1. Grundprinciper

1. ✅ Föredra exakt match alltid
2. 🔁 Tillåt rimliga ersättningar inom tydliga gränser
3. 📦 Tillåt kombination av förpackningar om nödvändigt
4. 🧠 Försök hitta ett bra alternativ om original saknas
5. ❌ Hoppa över om inget rimligt alternativ finns
6. 🧾 Alla avvikelser måste rapporteras till användaren

---

## 2. Regler för ersättning

### 2.1 Volym / Vikt

Tillåtna avvikelser:

* Upp till **±10 % skillnad** → OK
* Större volym → OK
* Mindre volym → endast om flera förpackningar kan kombineras

#### Exempel

| Begärt | Tillgängligt | Åtgärd                 |
| ------ | ------------ | ---------------------- |
| 500 g  | 450 g        | ❌ För litet            |
| 500 g  | 550 g        | ✅ OK                   |
| 500 g  | 2 × 250 g    | ✅ OK                   |
| 500 g  | 3 × 150 g    | ❌ För mycket avvikelse |

---

### 2.2 Fett- eller innehållshalt (ex. grädde)

Tillåtna avvikelser:

* Upp till **±10 procentenheter**
* Endast om användningsområdet är likvärdigt

#### Exempel

| Begärt      | Tillåtet            |
| ----------- | ------------------- |
| 40 % grädde | 36 % grädde ✅       |
| 40 % grädde | 30 % grädde ❌       |
| Vispgrädde  | Matlagningsgrädde ❌ |

---

### 2.3 Varumärkesbyte

Tillåtet om:

* Samma produkttyp
* Likvärdig kvalitet
* Ingen specialprodukt (eko, allergi, premium)

Prioritetsordning:

1. Samma varumärke
2. Kända alternativ
3. Budgetmärke

---

### 2.4 Produkt saknas helt

Om produkten inte finns:

1. Försök hitta **funktionellt alternativ**
2. Bedöm om alternativet rimligen fungerar i receptet
3. Om osäkert → **skippa**
4. Rapportera alltid

#### Exempel:

| Saknas          | Alternativ      | Beslut |
| --------------- | --------------- | ------ |
| Sriracha        | Sambal oelek    | ✅      |
| Färsk koriander | Fryst koriander | ⚠️     |
| Färsk dragon    | Torkad dragon   | ❌      |

---

## 3. Regler för kombination av produkter

Agenten får kombinera flera produkter om:

* Total volym uppnås
* Inte fler än 2–3 artiklar krävs
* Priset inte överstiger rimlig nivå

❌ Undvik:

* 3+ småförpackningar
* Orimligt högt totalpris

---

## 4. Hur användaren ska informeras

Alla avvikelser ska rapporteras tydligt efteråt.

### Format: Sammanfattning till användaren

#### ✅ Tillagt utan ändring

* Mjölk 1L – Arla
* Ägg 12-pack

#### 🔁 Ersatt

* Vispgrädde 40 % → Vispgrädde 36 %
* Champinjoner 200 g → Champinjoner 250 g

#### 📦 Kombinerat

* Parmesan 100 g → 2 × 50 g

#### ❌ Kunde inte läggas till

* Färsk koriander (inget rimligt alternativ hittades)

---

### Avslutande meddelande (alltid)

> 🧾 Varukorgen är klar.
> Jag har gjort några ersättningar – granska dem gärna innan du slutför köpet.

---

## 5. Agentens ansvar

Agenten ska:

* Vara konservativ i sina val
* Aldrig gissa vid osäkerhet
* Aldrig dölja ersättningar
* Aldrig genomföra köp

---

## 6. Rekommenderad standardinställning

```text
✔ Tillåt varumärkesbyte
✔ Tillåt +10 % volym
✔ Tillåt sammanslagning av förpackningar
✔ Tillåt rimliga ersättningar
✘ Tillåt inte köp
✘ Tillåt inte osäkra ersättningar
```

---

**Denna policy är avsedd att användas av AI-agenter som förbereder inköp – inte genomför dem.**
