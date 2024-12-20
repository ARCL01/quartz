#hidden 
## Procesy v operačním systému
- Vysvětli, co je to proces a jak se liší od programu.
- Jakými stavy prochází proces v rámci svého životního cyklu a které události způsobují změnu stavu procesu? V jakých frontách může proces čekat na své další zpracování?
- Jakou datovou strukturu o procesech udržuje OS? Co tato datová struktura obsahuje a k čemu všemu se používá?
- Jak se liší CPU Bound, I/O Bound procesy?
- Jaké typy plánovačů jsou použity pro plánování procesů a co je jejich úkolem?
## Odpověď
- ### **Vysvětli, co je to proces a jak se liší od programu.**
    - #### Proces
        - jakýkoliv program který je aktuálně vykonáván operačním systémem
    - #### Program
        - je soubor instrukcí uložený na disku, ten obsahuje kód, data a další informace potřebné k vykonání úkolu
    - Program je na rozdíl od procesu **pasivní**, samotný nevykonává žádnou činnost, dokud není načten a spuštěn operačním systémem jako proces
- ### **Jakými stavy prochází proces v rámci svého životního cyklu a které události stavu procesu?**
    - #### NEW
        - do tohoto stavu se proces dostane při vytvoření
    - #### READY
        - do tohoto stavu se proces dostane po vytvoření (**NEW**), při ukončení čekání na I/O, tedy ze stavu **WAITING**, nebo při přerušení ze stavu **RUNNING**
        - je-li proces v tomto stavu, nachází se **načtený** v paměti RAM
        - event který je volán při přesunu procesu do stavu **NEW** ze stavu **READY** je: **admitted**
    - #### RUNNING
        - do tohoto stavu se proces dostane jakmile prošel stavem **READY**
        - je-li proces v tomto stavu, je mu přiděleno místo na CPU a proces je **vykonáván**
        - event který je volán při přesunu procesu do stavu **RUNNING** ze stavu **READY** je: **preempted _(scheduler dispatch)_**
        - event který je volán při přesunu procesu ze stavu **RUNNING** do stavu **READY** je: **interrupt**
    - #### WAITING
        - do tohoto stavu se proces dostane požádá-li o přístup k I/O nebo jinému eventu, jeho výchozí stav je **RUNNING**
        - Jakmile je jeho žádost vyřešena vrací se do stavu **READY**
        - event který je volán při přesunu procesu ze stavu **RUNNING** do stavu **WAITING** je: **I/O or event wait**
        - event který je volán při přesunu procesu ze stavu **WAITING** do stavu **READY** je: **I/O or event completion**
    - #### TERMINATED
        - do tohoto stavu se proces dostane je-li dokončen, jeho výchozí stav je **RUNNING**
        - event který je volán při přesunu procesu ze stavu **RUNNING** do stavu **TERMINIATED** je: **exit**
    - #### ilustrační obrázek![[OPS/Maturitka Formalitka/Attachments/Stavy procesů.svg]]
- ### **V jakých frontách může proces čekat na své další zpracování?**
    - #### Job Queue
        - Procesy v této frontě čekají na přidělení místa v paměti RAM
        - Jsou to úlohy, které byly zadány do systému, ale ještě nebyly načteny do paměti.
        - **Přechod do této fronty**: Procesy vstupují do job queue, když jsou vytvořeny nebo zadány do systému. Zůstávají zde, dokud nejsou načteny do paměti.
    - #### Ready Queue
        - Procesy v této frontě čekají na přidělení CPU. Jsou připravené k vykonávání, ale momentálně nemají přidělené místo na procesoru
        - **Přechod do této fronty**: Proces přechází do této fronty ze stavu NEW po vytvoření nebo po návratu z čekání na I/O nebo jiné události.
        - tyto procesy jsou načteny v paměti RAM
    - #### I/O / Device Queue
        - Procesy v této frontě čekají na, dokončení I/O operace nebo jiného typu události.
        - **Přechod do této fronty**: Proces se dostane do této fronty, když žádá o I/O operaci nebo jinou událost a nemůže pokračovat, dokud tato operace není dokončena.
- ### **Jakou datovou strukturu o procesech udržuje OS? Co tato datová struktura obsahuje a k čemu všemu se používá?**
    - #### PCB (Process Control Block)
        - Každý proces je v operačním systému reprezentován takto
        - Skládá se z několika částí které obsahují informace o procesu
        - ##### Process state
            - Obsahuje stav procesu jako: NEW, READY, RUNNING, WAITING a TERMINATED
        - ##### Program counter
            - Obsahuje adresu další instrukce, kterou má proces vykonat
        - ##### CPU Register
            - Obsah registrů procesoru při posledním kontext switchi
        - ##### CPU-scheduling information
            - Obsahuje prioritu procesu a další informace potřebné pro scheduling jako CPU time _(čas který proces strávil na CPU)_
        - ##### Memory-management information
            - Obsahuje informace o alokovaném paměťovém prostoru procesu, jako jsou adresy zásobníku, hromadné paměti a segmentů.
        - ##### Accounting information
            - Uchovává informace o využití systémových prostředků, jako je celkový čas běhu, počet CPU cyklů,...
        - ##### I/O status information
            - Obsahuje informace o aktuálně používaných I/O zařízeních a jejich stavu
    - #### Context switching
        - Je způsob kterým OS, přepíná mezi více procesy, při přepínání procesů se do paměti RAM ukládá PCB aktuálně běžícího procesu a zároveň je načteno PCB procesu, na který OS přepíná.
- ### **Jak se liší CPU Bound, I/O Bound procesy?**
    - #### CPU Bound procesy
        - Tyto procesy tráví většinu svého času prováděním výpočtů a méně času na I/O operacích
        - **Delší** doba využití CPU s nízkou frekvencí opakování _(Long CPU bursts)_
    - #### I/O Bound procesy
        - Tyto procesy tráví většinu svého času prováděním I/O operací a méně času výpočty
        - **Kratší** doba využití CPU s vysokou frekvencí opakování _(Short CPU bursts)_
- ### **Jaké typy plánovačů jsou použity pro plánování procesů a co je jejich úkolem?**
    - #### Long-Term scheduler (job scheduler)
		- Hlavní úkolem je spravovat počet procesů které jsou povoleny v paměti v daný okamžik
        - Udržuje rovnováhu mezi CPU bound a I/O bound procesy
        - vybírá jaký proces by měl přejí do ready queue
        - pracuje pomaleji, je volán v řádech minut, sekund
    - #### Medium-Term scheduler
        - Hlavním úkolem je odstraňovat procesy z paměti, ukládat je na disk a později je znovu načítat _(swapping)_.
        - zasahuje v situaci když je v ready queue moc procesů
    - #### Short-Term scheduler (CPU scheduler)
        - Hlavním úkolem je pravidelně vybírat nový proces pro provedení na CPU
        - vybírá jakému procesu by mělo být přidělené místo na CPU
        - pracuje rychle, je volán v řádech milisekund
---
## Plánování procesoru
- Vysvětli, účel komponent CPU Scheduler a Dispatcher
- Z následujících čtyř algoritmů pro plánování procesoru si vyber dva a stručně vysvětli, jak fungují a jaké jsou jejich výhody, nevýhody.
    - First Come First Served _(FCFS)_
    - Shortest Job First _(SJF)_
    - Priority Scheduling _(PS)_
    - Round Robin Scheduling _(RR)_
## Odpověď
- ### **Vysvětli, účel komponent CPU Scheduler a Dispatcher**
    - #### CPU Scheduler _(short-term scheduler)_
        - Vybírá procesy z paměti RAM _(Ready queue)_ kterým bude přiděleno místo na CPU
        - Snaží se aby CPU bylo so nejvíce vytížené a minimalizuje dobu kdy je CPU nečinné
    - #### CPU Dispatcher
        - Přepíná kontext CPU na vybraný proces _(context switch)_.
            - Nejprve uloží PCB aktuálního procesu, poté načte PCB procesu vybraného CPU schedulerem
        - Musí pracovat rychle, čas který mu trvá k ukončení a zapnutí dalšího procesu se nazývá **dispatcher latency**
- ### **Z následujících čtyř algoritmů pro plánování procesoru si vyber dva a stručně vysvětli, jak fungují a jaké jsou jejich výhody, nevýhody.**
    - #### First Come First Served _(FCFS)_
        - Je nejjednodušší na implementaci a porozumění ze všech
        - **Nevýhodou** je, že proces, který vyžaduje delší práci CPU, může zdržet celou frontu. _(convoy effect)_
        - **Výhodou** je, že procesy, kterým jsou v ready queue jako **první**, jsou vyřešeny jako **první**
    - #### Shortest Job First _(SJF)_
        - Funguje na principu priority podle jejich času strávených na CPU _(CPU time/burst time)_, procesy které na CPU stráví nejméně času mají přednost
        - **Nevýhodou** je, že pokud se na procesor dostává hodně procesů které jsou krátké _(I/O bound procesy)_ může dojít k vyhladovění _(starvation)_ tím, že se na něj nedostanou procesy delší _(CPU bound procesy)_
        - **Výhodou** může být zvýšení throughput _(u)_, tím že se vykonávají první krátké procesy, dále snižuje průměrnou čekací dobu
    - #### Priority Scheduling _(PS)_
        - Funguje na principu velikosti priority procesu. Čím větší priorita procesu tím vyšší přednost.
        - Pokud mají dva procesy stejnou prioritu použije se FCFS
        - **Nevýhodou** je možnost vyhladovění _(starvation)_, kdy, pokud se v ready queue vyskytují procesy s obecně větší prioritou, nemusí se dostat na procesy s prioritou menší
    - #### Round Robin Scheduling _(RR)_
        - Funguje na principu přiřazování časového limit _(time quantum)_ který může proces strávit na CPU.
        - Ready queue funguje jako kruh, algoritmus přiřazuje jednotlivým procesům časové quantum, jeden proces je poslán na CPU, pokud je jeho _(burst time)_ větší než časové quantum CPU dispatcher provede **context switch** a vrací se do **ready queue**.
        - Je-li časové quantum moc **velké**, funguje stejně jako FCFS argotismus
        - Je-li časové quantum moc **malé**, nastane **overhead**, vzhledem k tomu, že pořád nastává **context switch**
---

