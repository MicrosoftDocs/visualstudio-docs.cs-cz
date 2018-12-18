---
title: 'Návod: Vyhledání nevrácené paměti (JavaScript) | Dokumentace Microsoftu'
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
- memory leaks, JavaScript example
ms.assetid: f595412f-776b-49a2-8433-ea0062c6904d
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2b84adac23547f42cca6113c5f5a7090f224e8c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51744954"
---
# <a name="walkthrough-find-a-memory-leak-javascript"></a>Návod: Vyhledání nevrácené paměti (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Tento názorný postup vás provede procesem identifikace a opravy problému s jednoduchou paměti pomocí analyzátoru paměti JavaScriptu. Analyzátor paměti jazyka JavaScript je k dispozici v aplikacích Visual Studio pro Windows Store vytvořená pro Windows pomocí jazyka JavaScript. V tomto scénáři vytvoříte aplikaci, která uchovává nesprávně elementů modelu DOM v paměti namísto disposing elementů v stejný kurz, ve kterém jsou vytvořeny.  
  
 Přestože příčinu nevracení paměti v této aplikaci je velmi specifický, zde uvedených kroků ukazují pracovní postup, který je pak izolovat objekty, které jsou nevrácení paměti obvykle efektivní.  
  
### <a name="running-the-javascript-memory-analyzer-test-app"></a>Spuštění aplikace pro testy analyzátor paměti jazyka JavaScript  
  
1.  V sadě Visual Studio, zvolte **souboru**, **nový**, **projektu**.  
  
2.  Zvolte **JavaScript** v levém podokně a pak zvolte **Windows**, **Windows 8**, pak buď **univerzální** nebo  **Windows Phone Apps**.  
  
    > [!IMPORTANT]
    >  Výsledky využití paměti v tomto tématu je testován vůči aplikaci pro Windows 8.  
  
3.  Zvolte **prázdnou aplikaci** šablonu projektu v prostředním podokně.  
  
4.  V **název** zadejte název, jako `JS_Mem_Tester`a klikněte na tlačítko **OK**.  
  
5.  V **Průzkumníka řešení**, otevřete soubor default.html a vložte následující kód mezi \<text > značky:  
  
    ```html  
    <div class="wrapper">  
        <div id="item"></div>  
        <button class="memleak" style="display: block" >Leak Memory</button>  
    </div>  
    ```  
  
    > [!IMPORTANT]
    >  Pokud používáte šablonu pro univerzální aplikace pro Windows 8.1, je potřeba aktualizovat kód HTML a CSS v obou. Windows a. WindowsPhone projekty.  
  
6.  Otevřete default.css a přidejte následující kód šablony stylů CSS:  
  
    ```css  
    .memleak {  
        position: absolute; top: 100px; left: 100px;  
    }  
    ```  
  
7.  Otevřete default.js a nahraďte celý kód s tímto kódem:  
  
    ```javascript  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var activation = Windows.ApplicationModel.Activation;  
  
        var wrapper;  
        var elem;  
  
        app.onactivated = function (args) {  
            if (args.detail.kind === activation.ActivationKind.launch) {  
                if (args.detail.previousExecutionState !== activation.ApplicationExecutionState.terminated) {  
                } else {  
                }  
                args.setPromise(WinJS.UI.processAll());  
  
                elem = document.getElementById("item");  
                wrapper = document.querySelector(".wrapper");  
                var btn = document.querySelector(".memleak");  
                btn.addEventListener("click", btnHandler);  
                run();  
            }  
        };  
  
        app.oncheckpoint = function (args) {  
        };  
  
        app.start();  
  
        function run() {  
            initialize();  
            load();  
        }  
  
        function initialize() {  
  
            if (wrapper != null) {  
                elem.removeNode(true);  
            }  
        }  
  
        function load() {  
  
            var newDiv = document.createElement("div");  
  
            newDiv.style.zIndex = "-1";  
            newDiv.id = "item";  
  
            wrapper.appendChild(newDiv);  
        }  
  
        function btnHandler(args) {  
            run();  
        }  
  
    })();  
    ```  
  
8.  Stisknutím klávesy F5 spusťte ladění. Ověřte, že **nevracení paměti** na stránce se zobrazí tlačítko.  
  
9. Přepněte zpět do sady Visual Studio (Alt + Tab) a klikněte na tlačítko Shift + F5 ukončete ladění.  
  
     Teď, když jste ověřili, že aplikace funguje, můžete prozkoumat využití paměti.  
  
### <a name="analyzing-the-memory-usage"></a>Analýza využití paměti  
  
1. Na **ladění** nástrojů v **spustit ladění** , zvolte cíl ladění pro aktualizovaný projekt: jednu emulátory Windows Phone nebo **simulátor**.  
  
   > [!TIP]
   >  Aplikace pro Windows Store, můžete také zvolit **místního počítače** nebo **vzdálený počítač** v tomto seznamu. Výhodou použití emulátoru nebo simulátoru je však, že můžete umístit u sady Visual Studio a snadno přepínat mezi běžící aplikaci a analýzu paměti jazyka JavaScript. Další informace najdete v tématu [spouštění aplikací v sadě Visual Studio](../debugger/run-store-apps-from-visual-studio.md) a [aplikace Windows Store spustit ve vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md).  
  
2. Na **ladění** nabídce zvolte **Profiler výkonu...** .  
  
3. V **dostupných nástrojů**, zvolte **paměti jazyka JavaScript**a klikněte na tlačítko **Start**.  
  
    V tomto kurzu budete se připojení analyzátoru paměti k spouštěný projekt. Informace o další možnosti, jako je připojení analyzátoru paměti nainstalované aplikace, najdete v části [paměti jazyka JavaScript](../profiling/javascript-memory.md).  
  
    Při spuštění analyzátoru paměti, může se zobrazit řízení uživatelských účtů, ke spuštění VsEtwCollector.exe. Zvolte **Ano**.  
  
4. Zvolte **nevracení paměti** tlačítko čtyřikrát za sebou.  
  
    Při výběru tlačítka, zpracování kódu v souboru default.js nemá práce, kterou povede k nevrácení paměti událostí. To budete používat pro diagnostické účely.  
  
   > [!TIP]
   >  Opakující se scénář, který chcete testovat nevracení paměti usnadňuje odfiltrovat nezajímavé informace, jako jsou objekty, které jsou přidány do haldy během inicializace aplikace nebo při načítání stránky.  
  
5. Ze spuštěné aplikaci přepněte do sady Visual Studio (Alt + Tab).  
  
    Analýzu paměti jazyka JavaScript informace zobrazí na nové kartě v sadě Visual Studio.  
  
    Graf paměti v tomto zobrazení se souhrnnými ukazuje využití paměti procesem v čase. Zobrazení poskytuje také příkazy jako **udělat snímek haldy**. Snímek poskytuje podrobné informace o využití paměti v určitou dobu. Další informace najdete v tématu [paměti jazyka JavaScript](../profiling/javascript-memory.md).  
  
6. Zvolte **udělat snímek haldy**.  
  
7. Přepněte do aplikace a zvolte možnost **nevracení paměti**.  
  
8. Přepněte do aplikace Visual Studio a zvolte **udělat snímek haldy** znovu.  
  
    Tento obrázek ukazuje snímek směrného plánu (#1) a snímek č. 2.  
  
    ![Směrný plán snímek a snímek 2](../profiling/media/js-mem-app-snapshot2.png "JS_Mem_App_Snapshot2")  
  
   > [!NOTE]
   >  Emulátor Windows Phone není uveden snímek aplikace v době pořízení snímku.  
  
9. Přepněte do aplikace a zvolte **nevracení paměti** tlačítko znovu.  
  
10. Přepněte do aplikace Visual Studio a zvolte **udělat snímek haldy** třetí.  
  
    > [!TIP]
    >  Pomocí třetí snímku v tomto pracovním postupu, se dá odfiltrovat změny z snímek směrného plánu na druhý snímek, které nejsou přidruženy k nevracení paměti. Například může být očekávané změny, jako je aktualizace záhlaví a zápatí stránky, které budou generovat některé změny využití paměti, ale pravděpodobně nemá vztah k nevracení paměti.  
  
     Tento obrázek ukazuje snímek č. 2 a snímek č. 3.  
  
     ![Snímek 2 a 3 snímek](../profiling/media/js-mem-app-snapshot3.png "JS_Mem_App_Snapshot3")  
  
11. V sadě Visual Studio, zvolte **Zastavit** zastavíte profilaci.  
  
12. V sadě Visual Studio porovnejte snímky. Snímek #2 obsahuje následující informace:  
  
    - Velikost haldy (zobrazené červeně na levé straně šipka nahoru) zvýšila o několik ve srovnání s snímku č. 1 KB.  
  
      > [!IMPORTANT]
      >  Využití hodnoty přesné paměti pro velikost haldy závisí na cíl ladění.  
  
    - Počet objektů na haldě (zobrazené červená šipka vpravo nahoru) bylo zvýšeno ve srovnání s snímku č. 1. Jeden objekt se přidala (+ 1) a byly odebrány žádné objekty (-0).  
  
      Snímek #3 zobrazuje následující:  
  
    - Velikost haldy se znovu zvýšila několik stovek bajtů ve srovnání s snímku č. 2.  
  
    - Počet objektů na haldě zvýšilo znovu ve srovnání s snímku č. 2. Jeden objekt se přidala (+ 1) a byly odebrány žádné objekty (-0).  
  
13. Ve snímku č. 3, vyberte text odkazu na pravé straně, který zobrazuje hodnotu + 1 / - 0 vedle červená šipka nahoru.  
  
     ![Odkaz na jiné zobrazení objektů haldy](../profiling/media/js-mem-app-link.png "JS_Mem_App_Link")  
  
     Tím se otevře rozdílové zobrazení objektů na haldě, volá **snímku č. 3 – snímek č. 2**, s typy zobrazení ve výchozím nastavení. Ve výchozím nastavení zobrazí se seznam objekty přidané do haldy mezi snímku č. 2 a snímek č. 3.  
  
14. V **oboru** filtrovat, zvolte **objekty přetrvávající ze snímku č. 2**.  
  
15. Otevření objektu HTMLDivElement v horní části stromu objektů, jak je znázorněno zde.  
  
     ![Počet rozdílové zobrazení objektu na haldě](../profiling/media/js-mem-app-typesdiff.png "JS_Mem_App_TypesDiff")  
  
     Toto zobrazení obsahuje užitečné informace o nevracení paměti, jako je následující:  
  
    - Toto zobrazení ukazuje prvek DIV s ID `item`, a uchovávané velikosti objektu je několik stovek bajtů (přesná hodnota se liší).  
  
    - Tento objekt je objekt zbylé ze snímku č. 2 a představuje potenciální nevrácená paměť.  
  
      Základní znalost aplikace pomáhá v tomto okamžiku: výběr **nevracení paměti** tlačítko by odeberte DIV element a přidat prvek, takže kód vypadá, že nepodporuje pracovat přímo (to znamená, že nevrací paměť). V další části vysvětluje, jak to opravit.  
  
    > [!TIP]
    >  V některých případech vyhledání objektu ve vztahu k `Global` objekt vám mohou pomoci identifikovat tohoto objektu. Chcete-li to provést, otevřete místní nabídku pro identifikátor a klikněte na tlačítko **zobrazit v zobrazení kořenů**.  
  
##  <a name="FixingMemory"></a> Opravte problém paměti  
  
1. Prozkoumat pomocí dat zobrazení pomocí profileru kód, který je zodpovědný za odebrání prvků modelu DOM s ID "položka". Vyvolá se v `initialize()` funkce.  
  
   ```javascript  
   function initialize() {  
  
       if (wrapper != null) {  
           elem.removeNode(true);  
       }  
   }  
   ```  
  
    `elem.removeNode(true)` se možná nebudou fungovat správně. Prozkoumejte, jak je kód do mezipaměti prvek modelu DOM a najít chyby; odkaz na prvek uložený v mezipaměti nejsou aktualizována.  
  
2. V souboru default.js, přidejte následující řádek kódu do funkce zatížení, bezprostředně před volání `appendChild`:  
  
   ```javascript  
   elem = newDiv;  
   ```  
  
    Tento kód aktualizuje odkaz na prvek uložený v mezipaměti, takže elementu je správně odebrat, když zvolíte **nevracení paměti** tlačítko. Kompletní kód pro funkci zatížení nyní vypadá takto:  
  
   ```javascript  
   function load() {  
  
       wrapper = document.querySelector(".wrapper");  
  
       var newDiv = document.createElement("div");  
  
       newDiv.style.zIndex = "-1";  
       newDiv.id = "item";  
       elem = newDiv;  
  
       wrapper.appendChild(newDiv);  
   }  
   ```  
  
3. Na **ladění** nabídce zvolte **výkon a Diagnostika**.  
  
4. V **dostupných nástrojů**, zvolte **paměti jazyka JavaScript**a klikněte na tlačítko **Start**.  
  
5. Postupujte stejným způsobem jako před pořizovat snímky tři. Tady jsou shrnuté kroky:  
  
   1. V aplikaci, zvolte **nevracení paměti** tlačítko čtyřikrát za sebou.  
  
   2. Přepněte do aplikace Visual Studio a zvolte **udělat snímek haldy** pro snímek směrného plánu.  
  
   3. V aplikaci, zvolte **nevracení paměti** tlačítko.  
  
   4. Přepněte do aplikace Visual Studio a zvolte **udělat snímek haldy** pro druhý snímek.  
  
   5. V aplikaci, zvolte **nevracení paměti** tlačítko.  
  
   6. Přepněte do aplikace Visual Studio a zvolte **udělat snímek haldy** pro třetí snímek.  
  
      Snímek #3 nyní zobrazuje velikost haldy jako **žádný nárůst** ze snímku č. 2 a objekt se počítají jako + 1 nebo -1, což znamená, že jeden objekty byl přidán a jeden objekt se odebrala. To je požadované chování.  
  
      Následující obrázek ukazuje snímek č. 2 a snímek č. 3.  
  
      ![Snímky zobrazující nevracení paměti dlouhodobého](../profiling/media/js-mem-app-fixed-snapshot3.png "JS_Mem_App_Fixed_Snapshot3")  
  
## <a name="see-also"></a>Viz také  
 [Paměť JavaScriptu](../profiling/javascript-memory.md)



