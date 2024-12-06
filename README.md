# Maturita Vault / Quartz 4.0

> [!TIP]
> Změnil jsem odkaz na stránku:  
> [https://arcl01.github.io/quartz/](https://arcl01.github.io/quartz/)

Toto je GitHub maturitního vaultu. Pokud neumíš s GitHubem, vůbec to nevadí, tady se nic zajímavého dít nebude. Pokud to půjde, budu dávat všechno na stránku, kde to bude „user friendly“ (jediné, co bych doporučil, je přečíst si [markdown editor](#✏️-markdown-editor) a [markdown syntax](#📜-markdown-syntax)). Avšak pokud umíš s GitHubem, nebo se rád něčemu přiučíš, níže v tomto textu najdeš pár zajímavých věcí.

## ✏️ Markdown editor
> [!IMPORTANT]
> Pokud by někdo chtěl dělat zápisy ve Wordu, nebudu mu v tom bránit. Stačí, když to pošlete na Discord do chatu. Já to klidně upravím, aby to šlo dát na stránku, a Wordovský soubor nahraju na GitHub, aby byl stáhnutelný (taktéž přidám na stránku odkaz odpovídající tomu souboru).  
> ALE byl bych VELICE vděčný, kdybyste se naučili pracovat s Markdownem. Bylo by to jednodušší pro mě, kdo to všechno spravuje, a mělo by to benefit i pro vás, že byste uměli zase něco nového.
>
> _Prosmyslete si to._

Určitě vás zajímá, v čem máte psát poznámky. Máte na výběr: buď si najdete jakýkoliv Markdown editor na webu, třeba [tento](https://stackedit.io/), nebo půjdete cestou programu. Pokud bych měl něco doporučit, tak [Obsidian](https://obsidian.md/download). Tutoriál, jak nainstalovat program, snad dávat nemusím.

## 📜 Markdown syntax
Takový rychlý tutorial, jak funguje markdown syntax.
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

To jen tak ve zkratce. Kdyby to někoho zajímalo, zde je odkaz na [celý syntax](https://help.obsidian.md/Editing+and+formatting/Basic+formatting+syntax). Dá se tam dělat spousta zajímavých věcí. Možná si říkáte, že se na to můžete vy..., že se další jazyk učit nebudete. Pokud ano, mám pro vás dvě věci:  
1. 😙🖕, lehčí jazyk snad neexistuje.  
2. Ale jinak v Obsidianu zmáčknete `CTRL+P` (na Macu asi `CMD+P`) a napíšete, co potřebujete.

## ✈️ Offline přístup
Budu se snažit a každý týden vytvořím release poznámek. Budou to zazipované soubory, které jsou ve složce `content`. Ty si můžete stáhnout do telefonu a prohlížet i bez internetu (Obsidian je i na telefon).  
Odkaz na release; [zde](https://github.com/ARCL01/quartz/releases)

## 🧪 Pokročilé věci
Pokud chcete být ✨fancy✨, existuje možnost, jak nahrávat soubory na GitHub. Můžete udělat tzv. fork a potom ho sem pushnout. Já, nebo někdo jiný, ho schválíme. Zní lákavě, ne? Zde je tedy krátký tutoriál, jak na to.

### GitHub (bez GUI)
Přejděte do složky, do které chcete soubory nakopírovat, a používejte příkazy (funguje na Windows i Macu):
1. Na GitHubu [vytvoříš fork](https://github.com/ARCL01/quartz/fork), nic neměn, jenom zmáčkni 'Create fork'
2. Na PC přejdeš do složky, kam chceš soubory stáhnout
3. ```git clone https://github.com/<tvé jméno>/quartz```
4. Ve složce najdeš složku content. Soubory měň nebo přidávej pouze tam, nikde jinde nic neměň (Hlavu vám neurvu, ale budeme to muset spolu opravovit).

Po úpravě souborů pokračujte takto:
1. ```git add .```
2. ```git commit -m "<popis co jsem přidal>"```
3. ```git push origin v4```
4. Přejdi ```git clone https://github.com/<tvé jméno>/quartz```
5. Na GitHubu přejdi k forku a nahoře klikni na ```Contribute```.
6. Přidej titulek: ```Fork pull request - <tvé jméno>```
7. Přidej popisek.
8. Klikni na ```Create pull request```.

Když upravíš soubory, nemusíš hned vytvářet pull request. Můžeš si jich nastřádat víc a až potom poslat vše najednou.

### GitHub (GUI)
Na toto nemám tutoriál, ale hádám, že postup bude podobný. Začátek je stejný – vytvoř si fork, který si nakopíruješ do PC a tam ho edituješ.

##🛠️ Pro správce
Buildování by mělo proběhnout při každém pushi. Teoreticky, když se něco změní v souborech pro webovku, mělo by se to znovu buildnout. Mám to otestováno jen s Markdown soubory. Nevím, jestli to samé funguje pro program webu. Pokud je něco, co mění program, mělo by se to buildnout lokálně a pushnout na Git. Pokud jde jen o MD soubory, stačí to udělat na GitHubu.
- Command pro update `npx quartz sync`
