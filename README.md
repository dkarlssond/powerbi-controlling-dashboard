#  Finansiell Styrning — Budget vs Utfall Dashboard

##  Projekt-Beskrivning

Interactive Power BI dashboard för budget-styrning och ekonomianalys. 
Visar budget vs utfall-varianser på department- och konto-nivå, 
med KPI-uppföljning och trendanalys över 3 år.

### Features
-  P&L-rapportering (Resultaträkning)
-  Budget vs Utfall med varianser i % och kronor
-  Department-nivå drill-down och jämförelse
-  KPI-kort: Totalt Budget, Totalt Actual, Vinstmarginal, Budget Achievement %
-  Trendanalys över 36 månader (2022-2024)
-  Säsongsvariation synlig (högre Q4, lägre sommaren)

## Teknologi

**Power BI Desktop** 
- DAX-formler (CALCULATE, DATEADD, DATESYTD, SUMX)
- Power Query för datarengöring
- Star-schema datamodellering (Data → Calendar, Departments, Accounts)
- Relationhantering (många-till-en)

##  Datakälla

- **Företag:** Fiktivt medelstort svenska företag
- **Period:** 2022-01 till 2024-12 (36 månader)
- **Departement:** 9 (Försäljning, Marknadsföring, Produktion, IT & Digital, HR, Logistik, Forskning & Utveckling, Kundservice, Ledning)
- **Budget-poster:** 8 (Intäkter, COGS, Personalkostnader, Marknadsföringskostnader, Teknik, Försäljningskostnader, Övriga driftskostnader, Avskrivningar)

##  Filer# powerbi-controlling-dashboard

##  Hur man använder

1. **Ladda ned Controlling.pbix**
2. **Öppna i Power BI Desktop** (gratis från powerbi.microsoft.com)
3. **Navigera tabben "Sida 1"** för att se det kompletta dashboarden
4. **Använd filtren** överst för att drill-down på department/månad

##  Key Insights från Data

- **Vinstmarginal:** 51% (Intäkter 1668 MSEK vs COGS -814 MSEK)
- **Budget Achievement:** 116% (Actual 210,98 vs Budget 182,19)
- **Största department:** Försäljning
- **Säsongsmönster:** Höga utgifter Q4 (jul/Black Friday), låga sommaren

##  DAX Formulas (Highlights)

```dax
-- Vinstmarginal
Gross Margin % = 
VAR Revenue = CALCULATE([Total Actual], Accounts[Account] = "Intäkter")
VAR COGS = CALCULATE([Total Actual], Accounts[Account] = "Kostnad för sålda varor")
RETURN IF(Revenue = 0, 0, (Revenue + COGS) / Revenue)

-- Budget-träff
Budget Achievement % = [Total Actual] / [Total Budget]

-- Samma månad förra året (year-over-year)
Actual SPLY = CALCULATE([Total Actual], DATEADD('Calendar'[Date], -12, MONTH))
```

##  Målgrupp

- **Controllers** — daglig styrning och rapportering
- **CFOs** — ekonomisk översikt och trend-analys
- **Business Analysts** — data-drivna beslutsunderlag
- **Ekonomichefer** — budget-uppföljning

##  Kontakt & Portfolio

**LinkedIn:** www.linkedin.com/in/daniel-karlsson-techonomix
**E-mail:** dkarlssond@gmail.com

---

**Senast uppdaterad:** [Datum du skapade detta]
