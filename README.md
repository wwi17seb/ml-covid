# ml-covid

> Coronafallzahlenvorhersage je Land aufgrund anderer potenzieller Einflussfaktoren

## Idee

Die Idee des Projektes ist die Berechnung/Vorhersage von Fallzahlen zu Covid-19 für Länder, die keine oder klar ersichtlich falsche Zahlen veröffentlichen.
Dazu sollen mehrere Faktoren betrachtet werden, wie etwa die wirtschaftlichen Gegebenheiten eines gewissen Landes und die daraus resultierende medizinische Versorgung.
Zu diesen wirtschaftlichen Daten sollen ebenfalls Informationen zur Bevölkerung, also dem Alter oder der Bevölkerungsdichte, verwendet werden, um eine potentiell verlässliche Vorhersage treffen zu können.

Zur Berechnung dieser Zahlen soll das _Supervised Learning_ zum Einsatz kommen, während Länder mit verlässlichen Zahlen (siehe Quellen) als Trainingsdaten verwendet werden sollen.

Zuvor jedoch soll mit Hilfe des _Unsupervised Learning_ eine Klassifikation der verschiedenen Länder erfolgen, um potentielle Trainings-Länder zu finden.

## Überblick Vorgehen
![Vorgehen](OverviewProcess.png)

## Aufbau Repository

Alle verwendeten Daten werden im `/data`-Ordner untergebracht.
Dabei werden diese zunächst als Rohdaten in `/data/raw` gespeichert und anschließend aufbereitet.

## Datenquellen

| Name                                                     | Quelle                                                                                                                             |
| -------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| COVID-19                                                 | [Johns Hopkins University & Medicine](https://github.com/CSSEGISandData/COVID-19)                                                  |
| Medical doctors (per 10,000)                             | [WHO](https://www.who.int/data/gho/data/indicators/indicator-details/GHO/medical-doctors-(per-10-000-population))                  |
| Population with basic handwashing facilities at home (%) | [WHO](https://www.who.int/data/gho/data/indicators/indicator-details/GHO/population-with-basic-handwashing-facilities-at-home-(-)) |
| Government expenditure on education, total (% of GDP)    | [World Bank](https://data.worldbank.org/indicator/SE.XPD.TOTL.GD.ZS)                                                               |
| Current health expenditure (% of GDP)                    | [World Bank](https://data.worldbank.org/indicator/SH.XPD.CHEX.GD.ZS)                                                               |
| Human Development Index                                  | [United Nations Development Programme](hdr.undp.org/en/indicators/137506)                                                          |
| BIP pro Kopf // allgemeine ökonomische Faktoren          | [World Development Indicators](http://wdi.worldbank.org/table/WV.1)                                                                |
| Democracy Index                                          | [Democracy Index](https://en.wikipedia.org/wiki/Democracy_Index)                                                                   |
| Haushaltsgröße                                           | [UN](https://population.un.org/Household/index.html)                                                                               |
| Ernährungsdaten                                          | [Unicef](https://www.kaggle.com/ruchi798/malnutrition-across-the-globe)                                                            |
| Lockdown (Typ und Datum (verallgemeinert))               | [Multiple Sources](https://www.kaggle.com/jcyzag/covid19-lockdown-dates-by-country)                                                |
| Reiseverhalten                                           | [World Development Indicators](http://wdi.worldbank.org/table/6.14)                                                                |
| Sterberate (allgemein)                                   | [World Development Indicators - Mortality](http://wdi.worldbank.org/table/2.18)                                                    |

Um die als _Submodule_ eingebundenen Daten zu laden/aktualisieren, muss der Befehl `git submodule update` ausgeführt werden.
Beim erstmaligen clonen des Repositories ist zuvor noch `git submodule init` auszuführen.

## Ideen für Features

| Allgemeine Kennzahlen                                | Quelle                                                                                                                                                    |
| ---------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| :ok: BIP pro Kopf // allgemeine ökonomische Faktoren | [World Development Indicators](http://wdi.worldbank.org/table/WV.1)                                                                                       |
| :soon: Einwohnerzahl                                 | [Population by Country - 2020](https://www.kaggle.com/tanuprabhu/population-by-country-2020) + [Our World In Data](https://github.com/owid/covid-19-data) |
| :ok: Tests                                           | [WorldOMeters - Coronavirus](https://www.worldometers.info/coronavirus/#ctabs-row) + [Our World In Data](https://github.com/owid/covid-19-data)           |
| :ok: Lockdown                                        | [COVID-19 Lockdown dates by country](https://www.kaggle.com/jcyzag/covid19-lockdown-dates-by-country)                                                     |
| :soon: Frauen und Entwicklung                        | [World Development Indicators](http://wdi.worldbank.org/table/WV.5)                                                                                       |
| :ok: Democracy Index                                 | [Democracy Index](https://en.wikipedia.org/wiki/Democracy_Index) / [EIU](https://www.eiu.com/public/topical_report.aspx?campaignid=democracyindex2019)    |
| :soon: Armutszahlen                                  | [World Development Indicators](http://wdi.worldbank.org/table/1.1) + [World Development Indicators](http://wdi.worldbank.org/table/1.2)                   |


| Features, die mit Fallzahlen korrelieren könnten                           | Quelle                                                                                                                                                                                                          |
| -------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| :ok: Reiseverhalten                                                        | [World Development Indicators](http://wdi.worldbank.org/table/6.14)                                                                                                                                             |
| :ok: Hygiene (-> Population with basic handwashing facilities at home (%)) | [WHO](https://www.who.int/data/gho/data/indicators/indicator-details/GHO/population-with-basic-handwashing-facilities-at-home-(-)) + [Our World In Data](https://github.com/owid/covid-19-data)                 |
| :ok: Durchschnittl. Haushaltsgröße                                         | [Diercke Weltaltlas](https://diercke.westermann.de/content/haushaltsgr%C3%B6%C3%9Fen-und-kulturerdteile-nach-kolb-und-j-newig-978-3-14-100700-8-254-1-0) + [UN](https://population.un.org/Household/index.html) |
| :question: Klima                                                           | [Countries Statistical Dataset](https://www.kaggle.com/aestheteaman01/covcsd-covid19-countries-statistical-dataset)                                                                                             |


| Features, die mit Todeszahlen korrelieren könnten | Quelle                                                                                                                                                                             |
| ------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| :ok: div. Faktoren Gesundheitssystem              | [World Development Indicators by Countries](https://www.kaggle.com/hn4ever/world-development-indicators-by-countries) + [Our World In Data](https://github.com/owid/covid-19-data) |
| :ok: Human Development Index                      | [United Nations Development Programme](hdr.undp.org/en/indicators/137506)                                                                                                          |
| Altersstruktur                                    | [Our World In Data](https://github.com/owid/covid-19-data)                                                                                                                         |
| :ok: Anzahl Ärzte                                 | [WHO](https://www.who.int/data/gho/data/indicators/indicator-details/GHO/medical-doctors-(per-10-000-population))                                                                  |
| :ok: Ernährungsdaten (Über-/Untergewicht)         | [Malnutrition across the globe](https://www.kaggle.com/ruchi798/malnutrition-across-the-globe)                                                                                     |
| :ok: Allgemeine Sterblichkeitsrate                | [World Development Indicators - Mortality](http://wdi.worldbank.org/table/2.18)                                                                                                    |

## Weitere potenzielle Datenquellen

| Quelle                                                                                                                                | Datensätze                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [CoVCSD - Covid-19 Countries Statistical Dataset](https://www.kaggle.com/aestheteaman01/covcsd-covid19-countries-statistical-dataset) | 95 Länder: Anzahl Fälle (täglich + Summe), Anzahl Tode (täglich + Summe), Fälle pro 1000 Einwohner, Anzahl Tests, Wetterdaten (Tagestemperatur [min, max, avg], Niederschlag, Nebel), Bevölerkungsstatistiken (Anzahl, Dichte, Median-Alter, Geschlechtsverteilung, Anteil über 65), Informationen zum Gesundheitssystem (Betten pro 1000 Einwohner, Lungenpatienten pro mio. Einwohner [weibl. & männl.], Lebenserwartung [weibl. & männl.]), Reisedaten (Aus- sowie Inlandstourismus)                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| [World Development Indicators](http://wdi.worldbank.org/table)                                                                        | Allgemeine Datensätze der Weltbank - Themen: Armut, Menschen, Umwelt, Wirtschaft, Länder und Märkte, Globale Vernetzungen                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| [Global Health Security Index](https://www.ghsindex.org/wp-content/uploads/2020/04/2019-Global-Health-Security-Index.pdf#page=26)     | Veröffentlichte Tabelle mit Bewertungen bzgl. Pandemiebekämpfung - Aufgeteilt in sechs Unterpunkte                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| [Malnutrition across the globe](https://www.kaggle.com/ruchi798/malnutrition-across-the-globe)                                        | Zu: Einkommen, Essensverschwendung, Unter- und Übergewicht, Verkümmerte, Anzahl unter 5 Jähriger                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| [Population by Country - 2020](https://www.kaggle.com/tanuprabhu/population-by-country-2020)                                          | Bevölkerungsdaten wie: Veränderung, Dichte, Landgröße, Migration, Fruchtbarkeitsrate, Median-Alter, Anteil urban/rural Lebender, Anteil an der Weltbevölkerung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| [Average Age of Countries](https://www.kaggle.com/divyansh22/average-age-of-countries)                                                | Median-Alter von 1950-2050 in 5 Jahres Intervallen                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| [COVID-19 Lockdown dates by country](https://www.kaggle.com/jcyzag/covid19-lockdown-dates-by-country)                                 | Startzeitpunkt eines Lockdown, Art des Lockdown (vollständig, teilweise)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| [World Development Indicators by Countries](https://www.kaggle.com/hn4ever/world-development-indicators-by-countries)                 | Datensätze: Gesundheit (Daten zu Raucher, Tuberkulose, Diabeter, HIV und Versterbensgrund), Landwirtschaft (Anteil der Fläche, Benutzungsart, Düngung), Klima (Anteil Land mit max. Höhenunterschied < 5m, Anteil Bevölkerung in diesen Gebieten [rural, urban], Risikovorbereitung/-bewältigung), Emissionen (Energieimporte Öl und BIP Anteil dazu, Daten zu CO2-Emissionen), Energie (Bevölkerungsanteil mit Strom [rural, urban], erneuerbare Energien), Frischwasser (Bezugsquellen, Erneuerbarkeit, Benutzung durch Bevölkerung), Treibhausgasemissionen (Gesamt, Methan, Stickoxide, Andere), Gesundheitssystem (Anteil Ausgaben an BIP, Eigenanteil Einwohner, Anteil Fachärzte pro 100.000 Einwohner, Vollständigkeit Geburts- sowie Sterberegister), Ländliche Gebiete (Aufteilung der Länder in Forst-, Landwirtschaft etc.), Nachhaltigkeit (Ältere Statistiken zu: Zugang zu sauberem Trinkwasser, Zugang zu Sanitäranlagen, Zugang zu Elektrizizät ...) |
