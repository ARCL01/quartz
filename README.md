# Maturita vault / Quartz 4.0
> [!TIP]
> Změnil jsem odkaz na stránku
> https://arcl01.github.io/quartz/

 Takže, toto je GitHub maturitního vaultu. Pokud neumíš s GitHubem, vůbec to nevadí, tady se nic zajímavého dít nebude. Pokud to půjde, budu dávat všechno na stránku, kde to bude 'user friendly' (jediné co bych doporučil si přečíst je [markdown editor](#%EF%B8%8F-markdown-editor) a [markdown syntax](-markdown-syntax)). Avšak, pokud umíš s GitHubem, nebo se něčemu rád přiučíš tak níže tady v tomto textu je pár zajímavých věcí.
 
## ✏️ Markdown editor
> [!IMPORTANT]
> Pokud by někdo chtěl dělat zápisy ve Wordu, nebudu mu v tom bránit, pokud to pošlete na Discord do chatu, já to klidně upravím aby to šlo dát na tu stránku a ten wordovský soubor nahraju na GitHub aby byl stáhnutelný (Taktéž přidám na stránku odkaz odpovídající tomu souboru).
> ALE byl bych VELICE ale velice vděčný, kdyby jste se naučili s markdownem, bylo by to jednodušší pro mě, který toto všechno musí spravovat a určitě by to mělo benefit i pro vás že byste uměli zase s něčím novým.
>
> _Prosmyslete si to_

Určitě vás zajímá v čem to máte jako psát ty poznámky, no tak máte na výběr, buď to si najde jaký koliv markdown editor na webu, třeba [toto](https://stackedit.io/) a nebo, půjdete cestou programu. Pokud bych vám měl doporučit něco já, tak je to [Obsidian](https://obsidian.md/download). Tutoriál jak nainstalovat program snad dávat nemusím...

## 📜 Markdown syntax
Takový rychlý tutorial jak funguje markdown syntax.
### Nadpisy
```
 # Nadpis 1
 ## Nadpis 2
 ### Nadpis 3
 ...
```
#### Takto to vypadá
 # Nadpis 1
 ## Nadpis 2
 ### Nadpis 3
 ---
### Odrážky
```
 - ahoj
 - jak se máš?
 1. mám se
 2. dobře
```
#### Takto to vypadá
 - ahoj
 - jak se máš?
 1. mám se
 2. dobře
---
### Styly
```
 _je to šikmo_ / *je to šikmo*
 **je to tlusté** / __je to tlusté__
 ==je to zvýrazněné== (na GitHubu to nefunguje)
 ~~je to přeškrtlé~~
 ***tlusté a šikmé*** / ___tlusté a šikmé___
```
#### Takto to vypadá
- _je to šikmo_ / *je to šikmo*
- **je to tlusté** / __je to tlusté__
- ==je to zvýrazněné== (na GitHubu to nefunguje)
- ~~je to přeškrtlé~~
- ***tlusté a šikmé*** / ___tlusté a šikmé___
 ---
To jen tak ve zkrtace, kdyby to někoho zajímalo, zde je odkaz na [syntax](https://help.obsidian.md/Editing+and+formatting/Basic+formatting+syntax). Možná si říkate že ne na to můžete vy..., že se další jazyk učit nebudete. Pokud ano, mám pro vás dvě věci.
1. 😙🖕
2. V obsidianu zmáčknete `CTRL+P` na macu asi `CMD+P`, napíšete co potřebujete.

## ✈️ Offline přístup
 Bude se snažit a každý týden budu dělat release poznámek, budou to zazipované soubory které jsou ve složce content, ty si můžete stáhout do telefonu a koukat na ně ikdyž nebudete mít internet (Obsidian je i na telefon). Odkaz na release [zde](https://github.com/ARCL01/quartz/releases)

## 🧪 Pokročilé věci
 Pokud chcete být ✨fancy✨, je zde ještě jedna možnost, jak nahávat soubory na GitHub. Můžete udělat tzv. fork a potom ho sem pushnout a já, nebo někdo jiný ho schválíme. Zní lákavě ne? Zde je tedy kartší tutoriál jak na to.
 - Nainstalujeme [GitHub for windows](https://git-scm.com/downloads/win) (bez GUI) nebo [GitHub Desktop](https://desktop.github.com/download/) (GUI), pokud jste jeden z mála co má mac, `brew install git`
### GitHub (bez GUI)
Přejděte do složky do které chceme soubory nakopírovata už jenom házejte příkazy (jak mac tak widle)
1. Na GitHubu [vytvoříš fork](https://github.com/ARCL01/quartz/fork), nic neměn, jenom zmáčkni 'Create fork'
2. Na PC přejdeš do složky kde chceš mít soubory
3. ```git clone https://github.com/<tvé jméno>/quartz```
4. Ve pullnuté složce najdeš složku `content`, soubory budeš měnit popřípadě přidávat pouze tam, nikde jinde nic měnit nebudeš.

Po úpravě souborů pokračujte takto
1. ```git add .```
2. ```git commit -m "<popis co jsem přidal>"```
3. ```git push origin v4```
4. Přejdi ```git clone https://github.com/<tvé jméno>/quartz```
5. Nahoře klikni na ```contribute```
6. Přidej titulek ```Fork pull request - <tvé jméno>```
7. Přidej popisek
8. ```Create pull request```

Když upravíš soubory tak hned nemusíš vytvářet pull request, můžeš si jich nastřádat více a až potom poslat vše najednou.
### GitHub (GUI)
Na toto nemám tutoriál ale hádám, že to bude podobné, začátek je stejný, musíš si vytvořit fork, který si potom nakopíruješ do PC a tam ho edituješ.

## 🛠️ Pro správce
Buildování by mělo proběhnout při každém pushi. Takže teoreticky když se něco změní v souborech pro tu webovku, tak by se to mělo buildnout znovu. Mám to otestováné jenom s markdown soubory, nevím jestli to samé funguje pro program té stránky. Takže pokud to je něco co mění program, tak by se to mělo buildnout na kompu a pushout na git, pokud to jsou jenom md soubory, tak to stačí udělat na gitu. 
- Command pro update `npx quartz sync`
