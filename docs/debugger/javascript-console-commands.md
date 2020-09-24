---
title: Příkazy konzoly JavaScriptu | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.topic: reference
helpviewer_keywords:
- JavaScript Console commands [UWP apps]
- JavaScript debugging, console [UWP apps]
- debugging JavaScript, console [UWP apps]
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- uwp
- cordova
ms.openlocfilehash: 301461caa15321b5a77f42872c93f52f3ec2c9c1
ms.sourcegitcommit: da7f093db52df5dcd67e0a030e616b307f0dc2a8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2020
ms.locfileid: "91211271"
---
# <a name="javascript-console-commands-in-visual-studio"></a>Příkazy konzoly JavaScriptu v aplikaci Visual Studio

Můžete použít příkazy k posílání zpráv a provádění dalších úloh v okně konzoly JavaScriptu sady Visual Studio. Příklady, které ukazují, jak používat toto okno, najdete v tématu [rychlý Start: ladění JavaScriptu](../debugger/quickstart-debug-javascript-using-the-console.md?view=vs-2017&preserve-view=true). Informace v tomto tématu se vztahují na Node.js aplikace, aplikace pro UWP a aplikace vytvořené pomocí Visual Studio Tools pro Apache Cordova.

Pokud je okno konzoly JavaScriptu zavřené, můžete ho otevřít při ladění v aplikaci Visual Studio výběrem možnosti **ladit**  >  **Windows**  >  **konzolu Windows JavaScript**.

> [!NOTE]
> Pokud okno není během ladicí relace k dispozici, ujistěte se, že typ ladicího programu je nastaven na **skript** ve vlastnostech ladění projektu.

Informace o používání konzoly nástroje Microsoft Edge Developer Tools najdete v [tomto tématu](/microsoft-edge/devtools-guide).

## <a name="console-object-commands"></a>příkazy objektů konzoly

Tato tabulka zobrazuje syntaxi pro `console` příkazy objektů, které lze použít v okně konzoly JavaScriptu nebo které můžete použít k posílání zpráv do konzoly z vašeho kódu. Tento objekt poskytuje několik forem, takže můžete v případě potřeby rozlišovat mezi informačními zprávami a chybovými zprávami.

`window.console.[command]`Pokud potřebujete zabránit možnému nejasnostem u místních objektů s názvem Console, můžete použít formulář s delšími příkazy.

> [!TIP]
> Starší verze sady Visual Studio nepodporují kompletní sadu příkazů. Pomocí technologie IntelliSense na objektu konzoly můžete získat rychlé informace o podporovaných příkazech.

|Příkaz|Popis|Příklad|
|-------------|-----------------|-------------|
|`assert(expression, message)`|Pokud `expression` se vyhodnotí jako **false**, pošle se zpráva.|`console.assert((x == 1), "assert message: x != 1");`|
|`clear()`|Vymaže zprávy z okna konzoly, včetně chybových zpráv skriptu, a také vymaže skript, který se zobrazí v okně konzoly. Nevymaže skript, který jste zadali do vstupní výzvy konzoly.|`console.clear();`|
|`count(title)`|Odesílá počet volání příkazu Count do okna konzoly. Každé volání Count je jednoznačně identifikováno jako volitelné `title` .<br /><br /> Existující položka v okně konzoly je určena `title` parametrem (Pokud je k dispozici) a aktualizována příkazem Count. Není vytvořena nová položka.|`console.count();`<br /><br /> `console.count("inner loop");`|
|`debug(message)`|Odešle `message` do okna konzoly.<br /><br /> Tento příkaz je stejný jako Console. log.<br /><br /> Objekty, které jsou předány pomocí příkazu, jsou převedeny na hodnotu řetězce.|`console.debug("logging message");`|
|`dir(object)`|Odešle zadaný objekt oknu konzoly a zobrazí ho v Vizualizér objektů. K prozkoumání vlastností v okně konzoly můžete použít Vizualizér.|`console.dir(obj);`|
|`dirxml(object)`|Odešle zadaný uzel XML `object` do okna konzoly a zobrazí jej jako strom uzlu XML.|`console.dirxaml(xmlNode);`|
|`error(message)`|Odešle `message` do okna konzoly. Text zprávy je červený a je uvozen symbolem chyby.<br /><br /> Objekty, které jsou předány pomocí příkazu, jsou převedeny na hodnotu řetězce.|`console.error("error message");`|
|`group(title)`|Spustí seskupení zpráv, které jsou odesílány do okna konzoly, a odešle volitelné `title` jako popisek skupiny. Skupiny mohou být vnořené a v okně konzoly se zobrazí ve stromovém zobrazení.<br /><br /> Příkazy Group * mohou zjednodušit zobrazení výstupu okna konzoly v některých scénářích, například při použití modelu komponenty.|`console.group("Level 2 Header");` <br /> `console.log("Level 2");` <br /> `console.group();` <br /> `console.log("Level 3");` <br /> `console.warn("More of level 3");` <br /> `console.groupEnd();` <br /> `console.log("Back to level 2");` <br /> `console.groupEnd();` <br /> `console.debug("Back to the outer level");`|
|`groupCollapsed(title)`|Spustí seskupení zpráv, které jsou odesílány do okna konzoly, a odešle volitelné `title` jako popisek skupiny. Skupiny, které se odesílají pomocí, `groupCollapsed` se ve výchozím nastavení zobrazí ve sbaleném zobrazení. Skupiny mohou být vnořené a v okně konzoly se zobrazí ve stromovém zobrazení.|Použití je stejné jako `group` příkaz.<br /><br /> Podívejte se na příklad `group` příkazu.|
|`groupEnd()`|Ukončí aktuální skupinu.<br /><br /> Požadavky:<br /><br /> Visual Studio 2013|Podívejte se na příklad `group` příkazu.|
|`info(message)`|Odešle `message` do okna konzoly. Zpráva je uvozena symbolem informací.|`console.info("info message");`<br /><br /> Další příklady najdete v části [formátování výstupu konzoly. log](#ConsoleLog) dále v tomto tématu.|
|`log(message)`|Odešle `message` do okna konzoly.<br /><br /> Pokud předáte objekt, tento příkaz odešle objekt do okna konzoly a zobrazí jej v Vizualizér objektů. K prozkoumání vlastností v okně konzoly můžete použít Vizualizér.|`console.log("logging message");`|
|`msIsIndependentlyComposed(element)`|Používá se ve webových aplikacích. Nepodporuje se v aplikacích pro UWP pomocí JavaScriptu.|Nepodporováno|
|`profile(reportName)`|Používá se ve webových aplikacích. Nepodporuje se v aplikacích pro UWP pomocí JavaScriptu.|Nepodporováno|
|`profileEnd()`|Používá se ve webových aplikacích. Nepodporuje se v aplikacích pro UWP pomocí JavaScriptu.|Nepodporováno|
|`select(element)`|Vybere zadaný kód HTML `element` v [Průzkumníku modelu DOM](../debugger/quickstart-debug-html-and-css.md).|Console. Select (element);|
|`time (name)`|Spustí časovač, který je identifikovaný nepovinným `name` parametrem. Při použití s nástrojem `console.timeEnd` vypočítá aplikace čas, který uplyne mezi `time` a a `timeEnd` pošle výsledek (měřeno v MS) do konzoly pomocí `name` řetězce jako předpony. Slouží k povolení instrumentace kódu aplikace pro měření výkonu.|`console.time("app start");  app.start();  console.timeEnd("app start");`|
|`timeEnd(name)`|Zastaví časovač, který je identifikovaný nepovinným `name` parametrem. Viz `time` příkaz konzoly.|`console.time("app start"); app.start(); console.timeEnd("app start");`|
|`trace()`|Odešle trasování zásobníku do okna konzoly. Trasování zahrnuje kompletní zásobník volání a obsahuje informace, jako je název souboru, číslo řádku a číslo sloupce.|`console.trace();`|
|`warn(message)`|Pošle `message` do okna konzoly, na kterém představí symbol upozornění.<br /><br /> Objekty, které jsou předány pomocí příkazu, jsou převedeny na hodnotu řetězce.|`console.warn("warning message");`|

## <a name="miscellaneous-commands"></a>Různé příkazy
Tyto příkazy jsou také k dispozici v okně konzoly JavaScriptu (nejsou k dispozici z kódu).

|Příkaz|Popis|Příklad|
|-------------|-----------------|-------------|
|`$0`, `$1`, `$2`, `$3`, `$4`|Vrátí zadaný prvek do okna konzoly. `$0` Vrátí prvek aktuálně vybraný v Průzkumníku modelu DOM, `$1` vrátí prvek dříve vybraný v Průzkumníku modelu DOM a tak dále, až do čtvrtého dříve vybraného elementu.|$3|
|`$(id)`|Vrátí prvek podle ID. Toto je příkaz zástupce pro `document.getElementById(id)` , kde `id` je řetězec, který představuje ID elementu.|`$("contenthost")`|
|`$$(selector)`|Vrátí pole prvků, které odpovídají zadanému selektoru pomocí syntaxe selektoru šablon stylů CSS. Toto je příkaz zástupce pro `document.querySelectorAll()` .|`$$(".itemlist")`|
|`cd()`<br /><br /> `cd(window)`|Umožňuje změnit kontext pro vyhodnocení výrazu z výchozího okna nejvyšší úrovně stránky na okno zadaného rámečku. Volání `cd()` bez parametrů vrátí kontext do okna nejvyšší úrovně.|`cd();`<br /><br /> `cd(myframe);`|
|`select(element)`|Vybere zadaný prvek v [Průzkumníku modelu DOM](../debugger/quickstart-debug-html-and-css.md).|`select(document.getElementById("element"));`<br /><br /> `select($("element"));`<br /><br /> `select($1);`|
|`dir(object)`|Vrátí Vizualizér pro zadaný objekt. K prozkoumání vlastností v okně konzoly můžete použít Vizualizér.|`dir(obj);`|

## <a name="checking-whether-a-console-command-exists"></a>Kontroluje se, jestli existuje příkaz konzoly.
Před tím, než se pokusíte ho použít, můžete ověřit, zda určitý příkaz existuje. Tento příklad kontroluje existenci `console.log` příkazu. Pokud `console.log` existuje, kód ho zavolá.

```javascript
if (console && console.log) {
    console.log("msg");
}

```

## <a name="examining-objects-in-the-javascript-console-window"></a>Kontrola objektů v okně konzoly JavaScriptu
Můžete pracovat s libovolným objektem, který je v oboru při použití okna konzoly jazyka JavaScript. Chcete-li zkontrolovat objekt mimo rozsah v okně konzoly, použijte `console.log` , `console.dir` nebo jiné příkazy z kódu. Alternativně můžete s objektem pracovat z okna konzoly, pokud je v rozsahu, nastavením zarážky v kódu (**zarážka**  >  **vložení bodu vložení**).

## <a name="formatting-consolelog-output"></a><a name="ConsoleLog"></a> Formátování výstupu konzoly. log
Pokud předáte více argumentů `console.log` , bude konzola považovat argumenty za pole a zřetězit výstup.

```javascript
var user = new Object();
user.first = "Fred";
user.last = "Smith";

console.log(user.first, user.last);
// Output:
// Fred Smith

```

`console.log` také podporuje substituční vzory "printf" k formátování výstupu. Pokud v prvním argumentu použijete substituční vzory, použijí se k nahrazení zadaných vzorů v pořadí, ve kterém se používají, další argumenty.

 Podporují se tyto substituční vzory:

- % s-řetězec% i-Integer% d – celé číslo% f-float% o-Object% b-Binary% x-šestnáctková hodnota% e-exponent

  Tady je několik příkladů použití vzorů pro nahrazování v nástroji `console.log` :

```javascript
var user = new Object();
user.first = "Fred";
user.last = "Smith";
user.age = 10.01;
console.log("Hi, %s %s!", user.first, user.last);
console.log("%s is %i years old!", user.first, user.age);
console.log("%s is %f years old!", user.first, user.age);

// Output:
// Hi, Fred Smith!
// Fred is 10 years old!
// Fred is 10.01 years old!
```

## <a name="see-also"></a>Viz také
- [Rychlý start: Ladění JavaScriptu](../debugger/quickstart-debug-javascript-using-the-console.md?view=vs-2017&preserve-view=true)
- [Rychlý start: Ladění kódu HTML a CSS](../debugger/quickstart-debug-html-and-css.md?view=vs-2017&preserve-view=true)
