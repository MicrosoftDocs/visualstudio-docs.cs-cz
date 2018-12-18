---
title: Příkazy konzoly jazyka JavaScript | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- JavaScript Console commands [Windows Store apps]
- JavaScript debugging, console [Windows Store apps]
- debugging JavaScript, console [Windows Store apps]
ms.assetid: 359e2b24-6bb7-48e7-8b55-b570df0cb774
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d62754dc881e42b2beada17379def19eb96abcda
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725333"
---
# <a name="javascript-console-commands"></a>Příkazy konzoly jazyka JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Příkazy můžete použít k odesílání zpráv a provádění dalších úloh v okně konzoly jazyka JavaScript sady Visual Studio. Příklady, které ukazují, jak pomocí tohoto okna najdete v tématu [rychlý start: ladění JavaScriptu](../debugger/quickstart-debug-javascript-using-the-console.md). Informace v tomto tématu se vztahují na aplikace Windows Store, Windows Phone Store, aplikací a aplikací vytvořených pomocí Visual Studio Tools pro Apache Cordova. Informace o podporovaných konzole příkazy v aplikace Cordova, naleznete v tématu [Debug Your App](http://msdn.microsoft.com/library/c2a4a1d4-a4e8-47ec-811f-ad207c54f4d1). Informace o použití konzoly v nástrojích Internet Explorer F12 najdete v tématu [v tomto tématu](http://msdn.microsoft.com/library/ie/dn255006.aspx).  
  
 Pokud je zavření okna konzoly jazyka JavaScript, lze jej otevřít při ladění v sadě Visual Studio výběrem **ladění** > **Windows** > **jazyka JavaScript Konzola**.  
  
> [!NOTE]
>  Pokud okno není k dispozici během relace ladění, ujistěte se, že typ ladicího programu je nastaven na **skript** ve vlastnostech ladění pro projekt.  
  
## <a name="console-object-commands"></a>příkazy konzoly objektu  
 Tato tabulka ukazuje syntaxi `console` objekt příkazy, můžete použít v okně konzoly jazyka JavaScript nebo, že můžete použít k odesílání zpráv do konzoly z vašeho kódu. Tento objekt obsahuje počtem formulářů, aby mohl rozlišit mezi informační zprávy a chybové zprávy, pokud chcete.  
  
 Můžete použít delší formě v příkazu `window.console.[command]` potřebujete nedocházelo k záměnám možné s místní objekty s názvem konzoly.  
  
> [!TIP]
>  Starší verze sady Visual Studio nepodporují kompletní sadu příkazů. Pomocí IntelliSense na objekt konzoly a získat rychlé informace o podporovaných příkazů.  
  
|Příkaz|Popis|Příklad|  
|-------------|-----------------|-------------|  
|`assert(expression, message)`|Odešle zprávu, pokud `expression` vyhodnotí jako **false**.|`console.assert((x == 1), "assert message: x != 1");`|  
|`clear()`|Vymaže zprávy z okna konzoly, včetně skriptu chybové zprávy a vymaže skript, který se zobrazí v okně konzoly. Nerušte zaškrtnutí políčka skript, který jste zadali do konzoly zadejte řádku.|`console.clear();`|  
|`count(title)`|Počet případů, kdy byl volán příkaz počet odešle do okna konzoly. Každé volání count je jedinečně identifikovaný nepovinný `title`.<br /><br /> Je identifikována existující položku v okně konzoly `title` parametr (pokud existuje) a aktualizovat pomocí příkazu count. Není vytvořena nová položka.|`console.count();`<br /><br /> `console.count("inner loop");`|  
|`debug(message)`|Odešle `message` do okna konzoly.<br /><br /> Tento příkaz se shoduje s console.log.<br /><br /> Objekty, které se předávají pomocí příkazu jsou převedeny na hodnotu řetězce.|`console.debug("logging message");`|  
|`dir(object)`|Odešle zadaný objekt do okna konzoly a zobrazí jej v vizualizéru objektu. Vizualizér můžete použít ke kontrole vlastností v okně konzoly.|`console.dir(obj);`|  
|`dirxml(object)`|Odešle zadaný uzel XML `object` do okna konzoly a zobrazí ho jako uzel stromu XML.|`console.dirxaml(xmlNode);`|  
|`error(message)`|Odešle `message` do okna konzoly. Text zprávy je červené a začíná symbolem k chybě.<br /><br /> Objekty, které se předávají pomocí příkazu jsou převedeny na hodnotu řetězce.|`console.error("error message");`|  
|`group(title)`|Spustí seskupení pro zprávy odeslané do okna konzoly a odešle nepovinný `title` jako popisek skupiny. Skupiny mohou být vnořené a zobrazí ve stromovém zobrazení v okně konzoly.<br /><br /> Příkazy skupiny * může usnadnit zobrazit výstup okna konzoly v některých případech, například když komponenta model se používá.|`console.group("Level 2 Header");` <br /> `console.log("Level 2");` <br /> `console.group();` <br /> `console.log("Level 3");` <br /> `console.warn("More of level 3");` <br /> `console.groupEnd();` <br /> `console.log("Back to level 2");` <br /> `console.groupEnd();` <br /> `console.debug("Back to the outer level");`|  
|`groupCollapsed(title)`|Spustí seskupení pro zprávy odeslané do okna konzoly a odešle nepovinný `title` jako popisek skupiny. Skupiny, které jsou odeslány pomocí `groupCollapsed` ve výchozím nastavení se nezobrazí v sbalené zobrazení. Skupiny mohou být vnořené a zobrazí ve stromovém zobrazení v okně konzoly.|Využití je stejný jako `group` příkazu.<br /><br /> Podívejte se na příklad pro `group` příkazu.|  
|`groupEnd()`|Ukončí aktuální skupinu.<br /><br /> Požadavky:<br /><br /> Visual Studio 2013|Podívejte se na příklad pro `group` příkazu.|  
|`info(message)`|Odešle `message` do okna konzoly. Zpráva je uvedena informace symbol.|`console.info("info message");`<br /><br /> Další příklady najdete v tématu [formátování výstupu console.log](#ConsoleLog) dále v tomto tématu.|  
|`log(message)`|Odešle `message` do okna konzoly.<br /><br /> Pokud předáte objektu, tento příkaz odešle tento objekt do okna konzoly a zobrazí jej v vizualizéru objektu. Vizualizér můžete použít ke kontrole vlastností v okně konzoly.|`console.log("logging message");`|  
|`msIsIndependentlyComposed(element)`|Používá se ve službě web apps. Není podporováno v aplikacích pro Store pomocí jazyka JavaScript.|Není podporováno.|  
|`profile(reportName)`|Používá se ve službě web apps. Není podporováno v aplikacích pro Store pomocí jazyka JavaScript.|Není podporováno.|  
|`profileEnd()`|Používá se ve službě web apps. Není podporováno v aplikacích pro Store pomocí jazyka JavaScript.|Není podporováno.|  
|`select(element)`|Vybere zadané HTML `element` v [Průzkumníka modelu DOM](../debugger/quickstart-debug-html-and-css.md).|Console.Select(element);|  
|`time (name)`|Spustí časovač, který je identifikován tak volitelného `name` parametru. Při použití s `console.timeEnd`, vypočítá čas, který uplyne mezi `time` a `timeEnd`a odešle výsledek (měřeno v ms) pomocí konzoly `name` řetězec jako předpony. Umožňuje povolit instrumentaci kód aplikace pro měření výkonu.|`console.time("app start");  app.start();  console.timeEnd("app start");`|  
|`timeEnd(name)`|Zastaví časovač, který je identifikován nepovinný `name` parametru. Zobrazit `time` příkazu konzoly.|`console.time("app start"); app.start(); console.timeEnd("app start");`|  
|`trace()`|Odešle trasování zásobníku v okně konzoly. Trasování obsahuje úplný zásobník volání a obsahuje informace, třeba číslo sloupce, název souboru a číslo řádku.|`console.trace();`|  
|`warn(message)`|Odešle `message` do okna konzoly uvedena symbolem upozornění.<br /><br /> Objekty, které se předávají pomocí příkazu jsou převedeny na hodnotu řetězce.|`console.warn("warning message");`|  
  
## <a name="miscellaneous-commands"></a>Další příkazy  
 Tyto příkazy jsou k dispozici také v okně konzoly jazyka JavaScript (nejsou k dispozici z kódu).  
  
|Příkaz|Popis|Příklad|  
|-------------|-----------------|-------------|  
|`$0`, `$1`, `$2`, `$3`, `$4`|Vrátí zadaný element v okně konzoly. `$0` Vrátí aktuálně vybraný v Průzkumníku modelu DOM, prvek `$1` vrátí dříve vybraný v Průzkumníku modelu DOM a tak dále, až na čtvrtý prvek dříve vybraný prvek.|$3|  
|`$(id)`|Vrátí element s ID. Jedná se o místní příkaz pro `document.getElementById(id)`, kde `id` je řetězec, který představuje ID elementu.|`$("contenthost")`|  
|`$$(selector)`|Vrátí pole prvků, které odpovídají zadaným selektor pomocí syntaxe selektor šablon stylů CSS. Jedná se o místní příkaz pro `document.querySelectorAll()`.|`$$(".itemlist")`|  
|`cd()`<br /><br /> `cd(window)`|Umožňuje změnit kontext pro vyhodnocení výrazu v okně zadaného rámce z okna nejvyšší úrovně výchozí stránky. Volání `cd()` bez parametrů vrátí kontext do okna nejvyšší úrovně.|`cd();`<br /><br /> `cd(myframe);`|  
|`select(element)`|Zadaný element v vybere [Průzkumníka modelu DOM](../debugger/quickstart-debug-html-and-css.md).|`select(document.getElementById("element"));`<br /><br /> `select($("element"));`<br /><br /> `select($1);`|  
|`dir(object)`|Vrátí vizualizér pro zadaný objekt. Vizualizér můžete použít ke kontrole vlastností v okně konzoly.|`dir(obj);`|  
  
## <a name="checking-whether-a-console-command-exists"></a>Kontroluje, zda existuje příkaz konzoly  
 Můžete zkontrolovat, jestli existuje ke konkrétnímu příkazu. před pokusem o jeho použití. Tento příklad kontroluje existenci `console.log` příkazu. Pokud `console.log` existuje, volá kód.  
  
```javascript  
if (console && console.log) {  
    console.log("msg");  
}  
  
```  
  
## <a name="examining-objects-in-the-javascript-console-window"></a>Zkoumání objektů v okně konzoly jazyka JavaScript  
 Budete moct setkat s libovolný objekt, který je v oboru při použití okna konzoly jazyka JavaScript. Chcete-li prověřit objekt mimo obor v okně konzoly, použijte `console.log` , `console.dir`, nebo dalších příkazů v kódu. Alternativně můžete pracovat s objektem z okna konzoly i když je v oboru, nastavením zarážky v kódu (**zarážku** > **vložit zarážku**).  
  
##  <a name="ConsoleLog"></a> Formátování výstupu console.log  
 Pokud předáte více argumentů `console.log`, bude považovat za pole argumentů a zřetězení výstup konzole.  
  
```javascript  
var user = new Object();  
user.first = "Fred";  
user.last = "Smith";  
  
console.log(user.first, user.last);  
// Output:  
// Fred Smith  
  
```  
  
 `console.log` také podporuje "printf" nahrazení způsoby formátování výstupu. Pokud používáte vzory pro nahrazení v prvním argumentu, další argumenty se použije k nahrazení zadaného vzorů v pořadí, ve kterém se používají.  
  
 Podporují se následující vzory pro nahrazení:  
  
- %s - string  
   %i – celé číslo  
   %d – celé číslo  
   %f - plovoucí desetinnou čárkou  
   %o – objekt  
   %b - binární  
   %x - šestnáctkové  
   %e - exponentu  
  
  Tady je několik příkladů použití vzorů pro nahrazení v `console.log`:  
  
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
 [Rychlý úvod: Ladění JavaScriptu](../debugger/quickstart-debug-javascript-using-the-console.md)   
 [Rychlý start: Ladění kódu HTML a CSS](../debugger/quickstart-debug-html-and-css.md)



