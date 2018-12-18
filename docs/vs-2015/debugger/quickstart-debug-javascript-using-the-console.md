---
title: 'Rychlý úvod: Ladění JavaScriptu pomocí konzoly | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.JavaScriptConsole
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- JavaScript Console
- JavaScript debugging
- debugging, JavaScript
ms.assetid: ea7adb71-52b6-4a5a-9346-98ca94b06bd7
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61f36594b4158c95621ec240fd7a883accd259a8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802593"
---
# <a name="quickstart-debug-javascript-using-the-console"></a>Rychlý úvod: Ladění JavaScriptu pomocí konzoly
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Použití okna konzoly jazyka JavaScript komunikovat a ladění aplikací pro Store vytvořených pomocí jazyka JavaScript. Tyto funkce jsou podporovány pro [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace Windows Phone Store, aplikací a aplikací vytvořených pomocí Visual Studio Tools pro Apache Cordova. Přehled příkazů konzoly, najdete v části [příkazy konzoly jazyka JavaScript](../debugger/javascript-console-commands.md).  
  
 Okno konzoly JavaScriptu umožňuje:  
  
- Odesílání objektů, hodnoty a zprávy z vaší aplikace v okně konzoly.  
  
- Zobrazit a upravit hodnoty místní a globální proměnné ve spuštěné aplikaci.  
  
- Zobrazení objektu vizualizéry.  
  
- Spuštění kódu jazyka JavaScript, který se spustí v rámci aktuální skriptovací kontext.  
  
- Zobrazení jazyka JavaScript chyby a výjimky, kromě výjimky Document Object Model (DOM) a prostředí Windows Runtime.  
  
- Proveďte další úlohy, jako je vymazání obrazovky. Zobrazit [příkazy konzoly jazyka JavaScript](../debugger/javascript-console-commands.md) pro úplný seznam příkazů.  
  
  V tomto tématu:  
  
- [Ladění pomocí okna konzoly jazyka JavaScript](#InteractiveConsole)  
  
- [Interaktivní režim ladění a přerušení](#InteractiveDebuggingBreakMode)  
  
- [Jednořádkový režim a víceřádkový režim v okně konzoly jazyka JavaScript](#SinglelineMultilineMode)  
  
- [Přepínání kontextu spuštění skriptu](#Switching)  
  
> [!TIP]
>  Pokud je zavření okna konzoly jazyka JavaScript, zvolte **ladění**>**Windows** > **konzoly jazyka JavaScript** znovu otevřít. V okně se zobrazí jenom při relaci ladění skriptu.  
  
 Pomocí okna konzoly jazyka JavaScript, můžete pracovat s vaší aplikací bez zastavení a restartování ladicího programu. Další informace najdete v tématu [aktualizace aplikace (JavaScript)](../debugger/refresh-an-app-javascript.md). Informace o další funkce, například pomocí Průzkumníka modelu DOM a nastavovat zarážky, ladění jazyka JavaScript naleznete v tématu [rychlý start: ladění kódu HTML a CSS](../debugger/quickstart-debug-html-and-css.md) a [ladění aplikací v sadě Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
##  <a name="InteractiveConsole"></a> Ladění pomocí okna konzoly jazyka JavaScript  
 Následujícím postupem se vytvoří `FlipView` aplikace a ukazují, jak interaktivně ladění JavaScriptu Chyba kódování.  
  
> [!CAUTION]
>  Ukázková aplikace je aplikace Windows Store. Nicméně funkce konzoly je zde popsáno, platí také pro aplikace vytvořené pomocí nástrojů Visual Studio pro Apache Cordova.  
  
#### <a name="to-debug-javascript-code-in-the-flipview-app"></a>Chcete-li ladit kód jazyka JavaScript v aplikaci FlipView  
  
1.  Vytvoření nového řešení v sadě Visual Studio výběrem **souboru** > **nový projekt**.  
  
2.  Zvolte **JavaScript** > **Store aplikace**, zvolte buď **aplikací Windows** nebo **aplikace Windows Phone**a klikněte na tlačítko  **Prázdná aplikace**.  
  
3.  Zadejte název projektu, například `FlipViewApp`a zvolte **OK** vytvořte aplikaci.  
  
4.  V elementu tělo default.html nahraďte stávající kód HTML s tímto kódem:  
  
    ```html  
    <div id="flipTemplate" data-win-control="WinJS.Binding.Template"  
             style="display:none">  
        <div class="fixedItem" >  
            <img src="#" data-win-bind="src: flipImg" />  
        </div>  
    </div>  
    <div id="fView" data-win-control="WinJS.UI.FlipView" data-win-options="{  
        itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">  
    </div>  
    ```  
  
5.  Otevřete default.css a přidat šablona stylů CSS pro `#fView` selektor:  
  
    ```css  
    #fView {  
        background-color:#0094ff;  
        height: 500px;  
        margin: 25px;  
    }  
    ```  
  
6.  Otevřete default.js a nahraďte kód následujícím kódem jazyka JavaScript:  
  
    ```javascript  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var activation = Windows.ApplicationModel.Activation;  
  
        var myData = [];  
        for (var x = 0; x < 4; x++) {  
            myData[x] = { flipImg: "/images/logo.png" }  
        };  
  
        var pages = new WinJS.Binding.List(myData, { proxy: true });  
  
        app.onactivated = function (args) {  
            if (args.detail.kind === activation.ActivationKind.launch) {  
                if (args.detail.previousExecutionState !==  
                activation.ApplicationExecutionState.terminated) {  
                    // TODO: . . .  
                } else {  
                    // TODO: . . .  
                }  
                args.setPromise(WinJS.UI.processAll());  
  
                updateImages();  
            }  
        };  
  
        function updateImages() {  
  
            pages.push(0, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223195" });  
            pages.push(1, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223196" });  
            pages.push(2, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
  
        };  
  
        app.oncheckpoint = function (args) {  
        };  
  
        app.start();  
  
        var publicMembers = {  
            items: pages  
        };  
  
        WinJS.Namespace.define("Data", publicMembers);  
  
    })();  
    ```  
  
7.  Pokud ještě není vybraná cíl ladění, zvolte **simulátor** nebo pro Windows Phone, **palec Emulator 8.1 WVGA 4, 512MB** z rozevíracího seznamu vedle položky **zařízení** tlačítko **ladění** nástrojů:  
  
     ![Seznam cílů ladění vyberte](../debugger/media/js-select-target.png "JS_Select_Target")  
  
8.  Stisknutím klávesy F5 spusťte ladicí program.  
  
     Spuštění aplikace, ale Image nebyly nalezeny. APPHOST chyby v okně konzoly jazyka JavaScript, týkají chybí obrázky.  
  
9. S `FlipView` aplikaci spuštěnou v simulátoru nebo emulátor telefonu, typ `Data.items` v konzole okna vstupní řádek (vedle položky ">>" symbol) a stiskněte klávesu Enter.  
  
     Vizualizér pro `items` objektu se zobrazí v okně konzoly. Znamená to, že `items` vytvořena instance objektu a je k dispozici v aktuální skriptovací kontext. V okně konzoly můžete kliknout na pomocí uzlů objektu k zobrazení hodnoty vlastností (nebo použijte klávesy se šipkami). Pokud kliknete na `items._data` objektu, jak vidíte na tomto obrázku, zjistíte, že jeho odkazy na zdroje bitové kopie jsou nesprávné, podle očekávání. Výchozí Image (logo.png) jsou stále k dispozici v objektu a existují chybí obrázky spolu s očekávané bitové kopie.  
  
     ![Okno konzoly jazyka JavaScript](../debugger/media/js-console-window.png "JS_Console_Window")  
  
     Všimněte si také, že existuje mnoho více položek v `items._data` objektů, než byste očekávali.  
  
10. Na příkazovém řádku zadejte `Data.items.push` a stiskněte klávesu Enter. V okně konzoly se zobrazí vizualizér pro `push` funkce, které je implementované v [!INCLUDE[winjs_long](../includes/winjs-long-md.md)] souboru projektu. V této aplikaci používáme `push` pro přidání správné položky. S trochou šetření pomocí technologie IntelliSense, si ukážeme, že budeme používat `setAt` nahradit výchozí Image.  
  
11. Chcete-li tento problém vyřešit interaktivně bez zastavení ladicí relace, otevřete default.js a vyberte tento kód z `updateImages` funkce:  
  
    ```javascript  
    pages.push(0, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223195" });  
    pages.push(1, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223196" });  
    pages.push(2, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
    ```  
  
     Zkopírujte a vložte tento kód do řádku vstup konzoly jazyka JavaScript.  
  
    > [!TIP]
    >  Při vkládání více řádků kódu do konzoly jazyka JavaScript vstup řádku, řádku konzoly vstup, automaticky se přepne do víceřádkového režimu. Můžete stisknout kombinaci kláves Ctrl + Alt + M víceřádkový režim zapnutí a vypnutí. Spustit skript v víceřádkový režim, stiskněte klávesy Ctrl + Enter nebo výběrem symbolu šipku v pravém dolním rohu okna. Další informace najdete v tématu [jednořádkový režim a víceřádkový režim v okně konzoly jazyka JavaScript](#SinglelineMultilineMode).  
  
12. Opravte `push` funkce se volá v příkazovém řádku nahrazení `pages.push` s `Data.items.setAt`. Opravený kód by měl vypadat takto:  
  
    ```javascript  
    Data.items.setAt(0, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223195" });  
    Data.items.setAt(1, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223196" });  
    Data.items.setAt(2, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
    ```  
  
    > [!TIP]
    >  Pokud chcete použít `pages` místo objektu `Data.items`, budete muset nastavit zarážku v kódu zachovat `pages` objekt v oboru.  
  
13. Výběrem symbolu zelená šipka pro spuštění skriptu.  
  
14. Stiskněte kombinaci kláves Ctrl + Alt + M řádku konzoly vstup přepnout do jednořádkového režimu, a klikněte na tlačítko **vymazat vstup** (na červenou "X") Chcete-li odstranit kód z výzvou k zadání.  
  
15. Typ `Data.items.length = 3` na řádku a potom stiskněte klávesu Enter. Z dat tím cizí prvky.  
  
16. Znovu zkontrolovat simulátor nebo emulátor telefonu a uvidíte, že jsou správné bitové kopie na správné `FlipView` stránky.  
  
17. V Průzkumníku modelu DOM se zobrazí aktualizovaná element DIV a můžete přejít do podstromu najít očekávané IMG prvky.  
  
18. Zastavit ladění zvolením **ladění** > **Zastavit ladění** nebo pomocí klávesy Shift + F5 a potom odstraňte zdrojový kód.  
  
     Pro dokončení default.html stránku obsahující opravíte ukázkový kód, naleznete v tématu [ukázkový kód pro ladění jazyka HTML, CSS a JavaScript](../debugger/debug-html-css-and-javascript-sample-code.md).  
  
##  <a name="InteractiveDebuggingBreakMode"></a> Interaktivní režim ladění a přerušení  
 Můžete používat zarážky a při použití nástroje, jako jsou okna konzoly jazyka JavaScript ladění JavaScriptu s vnořením do kódu. Pokud program, který běží v ladicí program narazí na zarážku, ladicí program dočasně pozastaví provádění programu. Když je spuštění pozastaveno, program se přepne z režimu spuštění do režimu přerušení. Může obnovit spuštění kdykoli.  
  
 Když je program v režimu přerušení, můžete spouštět skripty a příkazy, které jsou platné v aktuálním kontextu spuštění skriptu okna konzoly jazyka JavaScript. V tomto postupu budete používat pevné verzi `FlipView` aplikaci, kterou jste dříve vytvořili pro demonstraci použití režimu pozastavení.  
  
#### <a name="to-set-a-breakpoint-and-debug-the-app"></a>Nastavení zarážky a ladit aplikace  
  
1.  V souboru default.html `FlipView` aplikaci, kterou jste dříve vytvořili, otevřete místní nabídku pro `updateImages()` pracovat a klikněte na tlačítko **zarážku** > **vložit zarážku**.  
  
2.  Zvolte **místního počítače** nebo **palec Emulator 8.1 WVGA 4, 512MB** v rozevíracího seznamu vedle položky **spustit ladění** tlačítko **ladění** panel nástrojů.  
  
3.  Zvolte **ladění** > **spustit ladění**, nebo stiskněte klávesu F5.  
  
     Aplikace přejde do režimu přerušení, když spuštění dosáhne `updateImages()` funkce a aktuální řádek provádění programu je zvýrazněn žlutě.  
  
     ![Pomocí konzole jazyka JavaScript v režimu pozastavení](../debugger/media/js-breakmode.png "JS_BreakMode")  
  
     Můžete změnit hodnoty proměnných okamžitě ovlivnit stav programu bez ukončení aktuální relace ladění.  
  
4.  Typ `updateImages` na řádku a stisknutím klávesy Enter. Vizualizér pro funkce se zobrazí v okně konzoly.  
  
5.  Vyberte funkci v okně konzoly zobrazíte implementace funkce.  
  
     Následující obrázek znázorňuje okno konzoly v tomto okamžiku.  
  
     ![Okno konzoly jazyka JavaScript vizualizéru](../debugger/media/js-console-function-visualizer.png "JS_Console_Function_Visualizer")  
  
6.  Zkopírujte jeden řádek z funkce z okna výstup do výzvou k zadání a změňte hodnotu indexu na 3:  
  
    ```javascript  
    pages.setAt(3, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
    ```  
  
7.  Stiskněte klávesu Enter pro spuštění na řádek kódu.  
  
     Pokud chcete krokovat kód řádek po řádku, stisknutím klávesy F11 nebo stisknutím klávesy F5 pokračovat v provádění programu.  
  
8.  Stisknutím klávesy F5 pokračovat v provádění programu. `FlipView` Aplikace se zobrazí, a teď zobrazují všechny čtyři stránky některou k imagí jiné než výchozí.  
  
     Pokud chcete přepnout zpět do sady Visual Studio, stiskněte klávesu F12 nebo Alt + Tab.  
  
##  <a name="SinglelineMultilineMode"></a> Jednořádkový režim a víceřádkový režim v okně konzoly jazyka JavaScript  
 Výzvou k zadání okna konzoly jazyka JavaScript podporuje jednořádkový režim a víceřádkový režim. Interaktivní ladění postup v tomto tématu poskytuje příklad použití obou režimech. Můžete stisknout kombinaci kláves Ctrl + Alt + M, chcete-li přepnout mezi režimy.  
  
 Poskytuje jednořádkový režim vstupní historie. Vstupní historie můžete procházet pomocí kláves Šipka nahoru a Šipka dolů. Jednořádkový režim vymaže výzvou k zadání při spouštění skriptů. Spustit skript v jednořádkový mód, stiskněte klávesu Enter.  
  
 Víceřádkový režim nevymaže výzvou k zadání při spouštění skriptů. Když přepnout do jednořádkového režimu z víceřádkový režim, můžete vymazat vstupní řádek stisknutím kombinace kláves **vymazat vstup** (červená "X"). Spustit skript v víceřádkový režim, stiskněte klávesy Ctrl + Enter nebo výběrem symbolu šipku v pravém dolním rohu okna.  
  
##  <a name="Switching"></a> Přepínání kontextu spuštění skriptu  
 Okno konzoly JavaScriptu umožňuje interakci s jedno provedení kontext, který představuje jednu instanci hostitele webové platformy (WWAHost.exe), po jednom. V některých případech může aplikaci spustit další instanci hostitele, jako je například při použití `iframe`, kontrakt sdílení, webový pracovní proces, nebo `WebView` ovládacího prvku. Pokud je spuštěna jiná instance hostitele, můžete vybrat kontextu různých spuštění při spuštění aplikace tak, že vyberete kontextu spuštění v **cílové** seznamu.  
  
 Následující obrázek znázorňuje cílového seznamu v okně konzoly jazyka JavaScript.  
  
 ![Cílit na výběr v okně konzoly jazyka JavaScript](../debugger/media/js-console-target.png "JS_Console_Target")  
  
 Můžete také přepnout kontext spuštění pomocí `cd` příkaz, ale musíte znát název další kontext spuštění a pomocí odkazu musí být v rozsahu. **Cílové** seznam poskytuje lepší přístup k jiné kontexty provádění.  
  
##  <a name="BrowserSupport"></a> Prohlížeče a Platformní podpory  
 Okna konzoly jazyka JavaScript se nepodporuje na následujících platformách:  
  
-   [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] a aplikací pro Windows Phone Store v jazyce JavaScript a HTML  
  
-   Internet Explorer 11 a systémem [!INCLUDE[win81](../includes/win81-md.md)]  
  
-   Aplikace Internet Explorer 10 a systémem [!INCLUDE[win8](../includes/win8-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Ladění aplikací v sadě Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   
 [Příkazy konzoly jazyka JavaScript](../debugger/javascript-console-commands.md)   
 [Aktualizace aplikace (JavaScript)](../debugger/refresh-an-app-javascript.md)   
 [Klávesové zkratky](../debugger/keyboard-shortcuts-html-and-javascript.md)   
 [Ladění ukázkový kód HTML, CSS a JavaScript](../debugger/debug-html-css-and-javascript-sample-code.md)   
 [Rychlý start: Ladění kódu HTML a CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Ladění ovládacího prvku WebView](../debugger/debug-a-webview-control.md)   
 [Technická podpora a usnadnění přístupu](http://msdn.microsoft.com/library/tzbxw1af\(VS.120\).aspx)



