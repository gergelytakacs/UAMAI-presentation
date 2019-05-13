# UAMAIpresentation

SK: Mustra na prezentácie pre Ústav automatizácie, merania a aplikovanej informatiky (ÚAMAI), SjF STU v Bratislave. Mustra je vhodná na konferenčné a iné profesionálne prezentácie aj na obhajoby záverečných prác. Mustra obsahuje konfigurovateľné jazykové varianty a voliteľnú nadradenú organizačnú zložku.

EN: Beamer template and example for IAMAI, FME, STU in Bratislava.


## Špeciálne príkazy

Príkazy fungujú presne tak ako v LaTeX dokumentoch, ale tieto podklady obsahujú aj špeciálne príkazy na zjednodušenie tvorenie prezentácií. 

### Titulkový slide

Príkaz
```
\titleslide[vedúci]{jazyk}{logo}
```
vygeneruje titulný slide s názvom a podnázvom prezentácie a menom autora. Argument `{jazyk}` špecifikuje jazykovú variantu, dostupná je angličtina a slovenčina (`{EN}` alebo `{SK}`). Argument `{logo}` špecifikuje variantu uvedenej logotýpie organizačnej zložky. Dostupná je logotýpia pre univerzitu a pre fakultu  (`{STU}` alebo `{SjF}`). Nepovinný argument `[vedúci]` uvedie meno vedúceho záverečnej práce na slide a dátum prezentácie. V prípade že nevyužijete argument (`\titleslide{jazyk}{logo}`), tieto údaje nebudú uvedené na titulke.  Titulný slide sa nezapočítava do číslovania prezentácie.

### Záverečný slide - poďakovanie

Na zobrazenie štandardizovaného poďakovania použite príkaz
```
\thankyouslide{kontakt}{jazyk}
```
kde prvý povinný argument `{kontakt}` je emailová alebo webová adresa a druhý argument `{jazyk}` špecifikuje jazykovú variantu poďakovania, dostupná je angličtina a slovenčina (`{EN}` alebo `{SK}`). Záverečný slide sa nezapočítava do číslovania prezentácie.

## Hlavička a päta prezentácie

Hlavičku prezentácie môžete nastaviť príkazom 
```
\slideheader{jazyk}
```
kým pätu môžete nastaviť pomocou 
```
\slidefooter{jazyk}{logo}   
```
V prípade hlavičky príkaz  `{jazyk}` berie jeden argument špecifikuje jazykovú variantu logotýpie ÚAMAI, dostupná je angličtina a slovenčina (`{EN}` alebo `{SK}`). Pre pätu prvý argument  `{jazyk}` nastavuje jazykovú variantu organizačnej zložky a druhý argument `{logo}` samotnú organizačnú zložku. Dostupná je logotýpia pre univerzitu a pre fakultu  (`{STU}` alebo `{SjF}`). 

## Bibliografické citácie

Použitím zvyčajného príkazu `\cite{}` vložíte biblografickú citáciu do prezentácie. Citácia je generovaná v tvare autor-rok, teda napr. [Takács et al., 2019]. Na vygenerovanie samotných odkazov potrebujete databázový súbor BiBTeX (`*.bib`) a príkaz
```
\referencesslide{subor}{jazyk}
```
automaticky uvedie citované zdroje tak, že podľa potreby vytvorí viacero slideov a nezapočíta ich do celkového počtu strán prezentácie. Prvý argument `{subor}` je názov BiBTeX súbora bez prípony, kým argument  `{jazyk}` nastavuje jazykovú variantu nadpisu.

Tieto podklady nepoužívajú knižnicu `natbib` ale je definovaná vlastná verzia príkazu `\citep{}`. Príkaz zobrazí bibliografickú citáciu v texte so zelenou farbou a hranatými zátvorkami. Príkaz `\cite{}` pritom má nezmenenú funkcionality.

### Biber

Ak chcete ešte krajšie bibliografické citácie, musíte nakonfigurovať Biber namiesto BiBTeX-u. Potom na začiatku musíte zavolať príkaz
```
\bibliographyfile{subor}{jazyk}
```
kde prvý argument `{subor}` je názov databázového súbora s príponou, kým argument  `{jazyk}` nastavuje jazykovú variantu citácie v texte. Na konci potom môžete automaticky vygenerovať citácie pomocou príkazu
```
\referencesslidebiber{jazyk}
```
kde argument  `{jazyk}` nastavuje jazykovú variantu nadpisu. Príkaz podľa potreby vytvorí viacero slideov a nezapočíta ich do celkového počtu strán prezentácie. 

Hlavnou výhodou využitia Biber je príkaz
```
\footfullcite{citacia}
```
ktorá citáciu uvedie v päte dokumentu rovno pri premietaní, navyše to uvedie aj do zoznamu na konci. Príkaz potrebuje jeden argument presne ako `\cite{}`, je to označenie citácie. 

## Odpovede na otázky oponenta

V prípade záverečných prác študent dostane otázky od oponenta ešte pred obhajobou. Je dobrý nápad uviesť otázky a odpovede za podakovaním. Na toto slúži prostredie
```
\begin{reviewerquestions}{jazyk}

% Otazky a odpovede

\end{reviewerquestions}

```
argument  `{jazyk}` nastavuje jazykovú variantu nadpisu. V tomto prostredí môžete využívať hocijaké príkazy z LaTeX, t.j. môžete vložiť matematické výrazy alebo obrázky. Táto časť podobne ako poďakovanie alebo bibliografia sa potom nezapočítava do celkového počtu strán prezentácie.

### Dvojitý monitor

Pri profesionálnych prezentáciach je často využitá konfigurácia dvoch monitorov. Jeden monitor (projektor) je za prezentujúcim a druhý a menší monitor vidí prednášajúci. V tom prípade na druhom pomocnom monitore možné zobraziť aj inú informáciu ako to je uvedené v prezentácii. Ak chcete využit túto možnosť, treba používat príkaz
```
\dualscreen
```
a pre daný slide poznámky dávať do príkazu `\note{Moja poznamka...}`.

Na rozdiel od softvéru PowerPoint, počítač automaticky neporadí so situáciou keďže LaTeX vygeneruje PDF. Je potrebné konzultovať [tento návod](https://www.scivision.dev/beamer-latex-dual-display-pdf-notes/), ktorý uvedie spôsob využitia dvojitých monitorov pre prezentáciu pre operačné systémy (OS) Windows, Linux aj MacOS. 

Sofvér `pympress` je dostupný rovno ako [predpripravený inštalačný súbor](https://github.com/Cimbali/pympress/releases/) pre OS Windows. Stačí stiahnúť súbor a pustiť inštaláciu.




