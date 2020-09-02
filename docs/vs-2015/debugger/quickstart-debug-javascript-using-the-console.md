---
title: 'Rychlý Start: ladění JavaScriptu pomocí konzoly | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: a2256dfde39c761258ffb63ec6bbd9473e1be385
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687583"
---
# <a name="quickstart-debug-javascript-using-the-console"></a>Rychlý úvod: Ladění JavaScriptu pomocí konzoly
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Okno konzoly JavaScriptu můžete použít k interakci s a ladění aplikací pro Store sestavených pomocí JavaScriptu. Tyto funkce jsou podporované pro [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace, aplikace Windows Phone Storu a aplikace vytvořené pomocí Visual Studio Tools pro Apache Cordova. Referenční informace k příkazům konzoly najdete v tématu [příkazy konzoly jazyka JavaScript](../debugger/javascript-console-commands.md).  
  
 Okno konzoly JavaScriptu vám umožní:  
  
- Odešlete objekty, hodnoty a zprávy z vaší aplikace do okna konzoly.  
  
- Zobrazení a úprava hodnot místních a globálních proměnných ve spuštěné aplikaci.  
  
- Zobrazit vizualizace objektů.  
  
- Spustí kód JavaScriptu, který se spustí v rámci aktuálního kontextu skriptu.  
  
- Zobrazit chyby a výjimky JavaScriptu, kromě model DOM (Document Object Model) (DOM) a prostředí Windows Runtime výjimky.  
  
- Proveďte další úkoly, jako je vymazání obrazovky. Úplný seznam příkazů najdete v tématu [příkazy konzoly JavaScriptu](../debugger/javascript-console-commands.md) .  
  
  V tomto tématu:  
  
- [Ladění pomocí okna konzoly JavaScriptu](#InteractiveConsole)  
  
- [Interaktivní ladění a režim přerušení](#InteractiveDebuggingBreakMode)  
  
- [Jednořádkový a víceřádkový režim v okně konzoly JavaScriptu](#SinglelineMultilineMode)  
  
- [Přepínání kontextu spuštění skriptu](#Switching)  
  
> [!TIP]
> Pokud je okno konzoly JavaScriptu zavřené, otevřete ho tak, že kliknete na **ladit** > **Windows**  >  **konzolu Windows JavaScript** . Okno se zobrazí pouze během relace ladění skriptu.  
  
 Pomocí okna konzoly JavaScriptu můžete pracovat s aplikací bez zastavení a restartování ladicího programu. Další informace najdete v tématu [aktualizace aplikace (JavaScript)](../debugger/refresh-an-app-javascript.md). Informace o dalších funkcích ladění JavaScriptu, jako je použití Průzkumníka modelu DOM a nastavení zarážek, najdete v tématu [rychlý Start: ladění HTML a CSS](../debugger/quickstart-debug-html-and-css.md) a [ladění aplikací v aplikaci Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
## <a name="debug-by-using-the-javascript-console-window"></a><a name="InteractiveConsole"></a> Ladění pomocí okna konzoly JavaScriptu  
 Následující postup vytvoří `FlipView` aplikaci a ukáže, jak interaktivně ladit chybu kódování JavaScriptu.  
  
> [!CAUTION]
> Ukázková aplikace je tady aplikace pro Windows Store. Níže popsané funkce konzoly se ale vztahují i na aplikace vytvořené pomocí Visual Studio Tools pro Apache Cordova.  
  
#### <a name="to-debug-javascript-code-in-the-flipview-app"></a>Ladění kódu JavaScriptu v aplikaci FlipView  
  
1. Vytvořte nové řešení v aplikaci Visual Studio tak, že kliknete na **soubor**  >  **Nový projekt**.  
  
2. Zvolte **JavaScript**  >  **aplikace pro obchod**s JavaScriptem, zvolte **aplikace pro Windows** nebo **aplikace Windows Phone**a pak zvolte **prázdná aplikace**.  
  
3. Zadejte název projektu, například `FlipViewApp` , a kliknutím na **tlačítko OK** vytvořte aplikaci.  
  
4. V prvku tělo default.html nahraďte existující kód HTML tímto kódem:  
  
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
  
5. Otevřete default. CSS a přidejte CSS pro `#fView` selektor:  
  
    ```css  
    #fView {  
        background-color:#0094ff;  
        height: 500px;  
        margin: 25px;  
    }  
    ```  
  
6. Otevřete default.js a nahraďte kód následujícím kódem JavaScriptu:  
  
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
  
7. Pokud cíl ladění již není vybrán, vyberte **simulátor** nebo pro Windows Phone **emulátor 8,1 WVGA 4 palce 512 MB** z rozevíracího seznamu vedle tlačítka **zařízení** na panelu nástrojů **ladění** :  
  
     ![Vybrat cílový seznam pro ladění](../debugger/media/js-select-target.png "JS_Select_Target")  
  
8. Stisknutím klávesy F5 spusťte ladicí program.  
  
     Aplikace se spustí, ale chybí obrázky. APPHOST chyby v okně konzoly JavaScriptu označují, že chybí obrázky.  
  
9. V `FlipView` aplikaci spuštěné v simulátoru nebo v emulátoru telefonu zadejte `Data.items` do pole vstupní výzva okna konzoly (vedle symbolu ">>") a stiskněte klávesu ENTER.  
  
     `items`V okně konzoly se zobrazí Vizualizér pro daný objekt. To znamená, že `items` objekt je vytvořen a je k dispozici v kontextu aktuálního skriptu. V okně konzoly můžete kliknutím na uzly objektu zobrazit hodnoty vlastností (nebo použít klávesy se šipkami). Pokud kliknete na tlačítko dolů k `items._data` objektu, jak vidíte na tomto obrázku, zjistíte, že odkazy na zdroje obrázků jsou nesprávné, podle očekávání. Výchozí obrázky (logo.png) jsou stále k dispozici v objektu a chybí obrázky s očekávanými obrázky.  
  
     ![Okno konzoly JavaScriptu](../debugger/media/js-console-window.png "JS_Console_Window")  
  
     Všimněte si také, že v objektu existuje mnoho dalších položek, `items._data` než byste očekávali.  
  
10. Na příkazovém řádku zadejte `Data.items.push` a stiskněte klávesu ENTER. Okno konzoly zobrazuje Vizualizér pro `push` funkci, která je implementována v [!INCLUDE[winjs_long](../includes/winjs-long-md.md)] souboru projektu. V této aplikaci používáme `push` k přidání správných položek. Při malém šetření pomocí technologie IntelliSense zjistíme, že je vhodné použít `setAt` k nahrazení výchozích imagí.  
  
11. Chcete-li tento problém vyřešit interaktivně bez zastavení relace ladění, otevřete default.js a vyberte tento kód z `updateImages` funkce:  
  
    ```javascript  
    pages.push(0, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223195" });  
    pages.push(1, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223196" });  
    pages.push(2, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
    ```  
  
     Zkopírujte a vložte tento kód do vstupní výzvy konzoly JavaScriptu.  
  
    > [!TIP]
    > Když vložíte více řádků kódu do vstupní výzvy konzoly jazyka JavaScript, bude vstupní výzva konzoly automaticky přepnuta do víceřádkového režimu. Stisknutím kombinace kláves CTRL + ALT + M můžete zapnout nebo vypnout víceřádkový režim. Chcete-li spustit skript v víceřádkovém režimu, stiskněte klávesy CTRL + ENTER nebo zvolte symbol šipky v pravém dolním rohu okna. Další informace naleznete v části [jednořádkový režim a víceřádkový režim v okně konzoly JavaScriptu](#SinglelineMultilineMode).  
  
12. Opravte `push` volání funkcí v příkazovém řádku a nahraďte ji `pages.push` `Data.items.setAt` . Opravený kód by měl vypadat takto:  
  
    ```javascript  
    Data.items.setAt(0, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223195" });  
    Data.items.setAt(1, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223196" });  
    Data.items.setAt(2, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
    ```  
  
    > [!TIP]
    > Chcete-li použít `pages` objekt namísto `Data.items` , je nutné nastavit zarážku v kódu pro zachování `pages` objektu v oboru.  
  
13. Vyberte zelený symbol šipky ke spuštění skriptu.  
  
14. Stisknutím kombinace kláves CTRL + ALT + M Přepněte vstupní výzvu konzoly na jednořádkový režim a pak zvolte možnost **Vymazat vstup** (červený symbol "X") a odstraňte kód ze vstupní výzvy.  
  
15. Do `Data.items.length = 3` příkazového řádku zadejte a stiskněte klávesu ENTER. Tím se z dat odstraní nadbytečné prvky.  
  
16. Zkontrolujte simulátor nebo emulátor telefonu znovu a uvidíte, že jsou správné obrázky na správných `FlipView` stránkách.  
  
17. V Průzkumníku modelu DOM vidíte aktualizovaný element DIV a můžete přejít do podstromu a najít očekávané elementy IMG.  
  
18. Zastavení ladění kliknutím na **ladění**  >  **Zastavit ladění** nebo stisknutím SHIFT + F5 a opravte zdrojový kód.  
  
     Kompletní default.htmovou stránku obsahující opravený vzorový kód naleznete v tématu [ladění kódu HTML, CSS a JavaScript Code Sample](../debugger/debug-html-css-and-javascript-sample-code.md).  
  
## <a name="interactive-debugging-and-break-mode"></a><a name="InteractiveDebuggingBreakMode"></a> Interaktivní ladění a režim přerušení  
 Zarážky a krok do kódu lze použít při použití ladicích nástrojů JavaScriptu jako okna konzoly jazyka JavaScript. Když program, který je spuštěn v ladicím programu, narazí na zarážku, ladicí program dočasně pozastaví provádění programu. Po pozastavení běhu se program přepne z režimu spuštění do režimu přerušení. Můžete kdykoli pokračovat v provádění.  
  
 Když je program v režimu pozastavení, můžete použít okno konzoly JavaScriptu ke spouštění skriptů a příkazů, které jsou platné v aktuálním kontextu spuštění skriptu. V tomto postupu použijete pevnou verzi `FlipView` aplikace, kterou jste vytvořili dříve, abyste ukázali použití režimu přerušení.  
  
#### <a name="to-set-a-breakpoint-and-debug-the-app"></a>Nastavení zarážky a ladění aplikace  
  
1. V souboru default.html `FlipView` aplikace, kterou jste vytvořili dříve, otevřete místní nabídku pro `updateImages()` funkci a pak zvolte **zarážka**  >  **Vložit**zarážku.  
  
2. V rozevíracím seznamu vedle tlačítka **Spustit ladění** na panelu nástrojů **ladění** vyberte **místní počítač** nebo **emulátor 8,1 WVGA 4 palce 512 MB** .  
  
3. Zvolte **ladění**  >  **Spustit ladění**nebo stiskněte klávesu F5.  
  
     Aplikace přejde do režimu přerušení, pokud provádění dosáhne `updateImages()` funkce a aktuální řádek provádění programu je zvýrazněn žlutě.  
  
     ![Použití režimu přerušení v konzole jazyka JavaScript](../debugger/media/js-breakmode.png "JS_BreakMode")  
  
     Hodnoty proměnných můžete změnit tak, aby okamžitě ovlivnily stav programu bez ukončení aktuální relace ladění.  
  
4. Do `updateImages` příkazového řádku zadejte a stiskněte klávesu ENTER. V okně konzoly se zobrazí Vizualizér funkce.  
  
5. Vyberte funkci v okně konzoly, aby se zobrazila implementace funkce.  
  
     Následující obrázek znázorňuje okno konzoly v tomto okamžiku.  
  
     ![Okno konzoly JavaScriptu znázorňující Vizualizér](../debugger/media/js-console-function-visualizer.png "JS_Console_Function_Visualizer")  
  
6. Zkopírujte jeden řádek funkce z okna výstup do vstupní výzvy a změňte hodnotu indexu na 3:  
  
    ```javascript  
    pages.setAt(3, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
    ```  
  
7. Stisknutím klávesy ENTER spustíte řádek kódu.  
  
     Chcete-li krokovat kód řádek po řádku, stiskněte klávesu F11 nebo stiskněte klávesu F5 a pokračujte v provádění programu.  
  
8. Stisknutím klávesy F5 pokračujte v provádění programu. `FlipView`Zobrazí se aplikace a teď všechny čtyři stránky zobrazují jednu z jiných než výchozích imagí.  
  
     Chcete-li přejít zpět k aplikaci Visual Studio, stiskněte klávesu F12 nebo ALT + TAB.  
  
## <a name="single-line-mode-and-multiline-mode-in-the-javascript-console-window"></a><a name="SinglelineMultilineMode"></a> Jednořádkový a víceřádkový režim v okně konzoly JavaScriptu  
 Vstupní výzva pro okno konzoly JavaScriptu podporuje jednořádkový režim a víceřádkový režim. Postup interaktivního ladění v tomto tématu poskytuje příklad použití obou režimů. Stisknutím kombinace kláves CTRL + ALT + M můžete přepínat mezi jednotlivými režimy.  
  
 Jednořádkový režim poskytuje historii vstupu. Můžete procházet historii vstupu pomocí kláves Šipka nahoru a šipka dolů. Jednořádkový režim vymaže vstupní výzvu při spuštění skriptů. Pokud chcete skript spustit v režimu single-line, stiskněte klávesu ENTER.  
  
 Víceřádkový režim nevymaže vstupní výzvu při spuštění skriptů. Když přepnete do jednořádkového režimu z víceřádkového režimu, můžete odstranit vstupní řádek stisknutím klávesy **clear Input** (červený symbol "X"). Chcete-li spustit skript v víceřádkovém režimu, stiskněte klávesy CTRL + ENTER nebo zvolte symbol šipky v pravém dolním rohu okna.  
  
## <a name="switching-the-script-execution-context"></a><a name="Switching"></a> Přepínání kontextu spuštění skriptu  
 Okno konzoly JavaScriptu umožňuje interakci s jediným kontextem spuštění, který představuje jednu instanci hostitele webové platformy (WWAHost.exe) současně. V některých scénářích může vaše aplikace spustit jinou instanci hostitele, například při použití `iframe` , sdílení kontraktu, webového pracovního procesu nebo `WebView` ovládacího prvku. Pokud je spuštěná jiná instance hostitele, můžete při spuštění aplikace vybrat jiný kontext spuštění, a to tak, že v seznamu **cíl** vyberete kontext spuštění.  
  
 Následující ilustrace znázorňuje cílový seznam v okně konzoly JavaScriptu.  
  
 ![Výběr cíle v okně konzoly JavaScriptu](../debugger/media/js-console-target.png "JS_Console_Target")  
  
 Kontext spuštění můžete také přepnout pomocí `cd` příkazu, ale je nutné znát název dalšího kontextu spuštění a odkaz, který použijete, musí být v oboru. **Cílový** seznam poskytuje lepší přístup k dalším kontextům spuštění.  
  
## <a name="browser-and-platform-support"></a><a name="BrowserSupport"></a> Podpora prohlížečů a platforem  
 Okno konzoly JavaScriptu je podporované na následujících platformách:  
  
- [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] a aplikace Windows Phone Storu pomocí JavaScriptu a HTML  
  
- Internet Explorer 11 běžící na [!INCLUDE[win81](../includes/win81-md.md)]  
  
- Internet Explorer 10 běžící na [!INCLUDE[win8](../includes/win8-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Ladění aplikací v aplikaci Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   
 [Příkazy konzoly JavaScriptu](../debugger/javascript-console-commands.md)   
 [Aktualizace aplikace (JavaScript)](../debugger/refresh-an-app-javascript.md)   
 [Klávesové zkratky](../debugger/keyboard-shortcuts-html-and-javascript.md)   
 [Ladění ukázkového kódu HTML, CSS a JavaScript](../debugger/debug-html-css-and-javascript-sample-code.md)   
 [Rychlý Start: ladění HTML a CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Ladění ovládacího prvku WebView](../debugger/debug-a-webview-control.md)   
 [Podpora produktu a usnadnění](https://msdn.microsoft.com/library/tzbxw1af\(VS.120\).aspx)
