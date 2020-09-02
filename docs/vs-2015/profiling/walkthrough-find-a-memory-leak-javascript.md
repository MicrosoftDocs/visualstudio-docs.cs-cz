---
title: 'Návod: Vyhledání nevrácené paměti (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 5617dc6cbe4b7ba096afe1f308d06e7f4aaf9c6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64785518"
---
# <a name="walkthrough-find-a-memory-leak-javascript"></a>Návod: Vyhledání nevrácené paměti (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Tento návod vás provede procesem identifikace a řešení problému s jednoduchou pamětí pomocí nástroje JavaScript Memory Analyzer. Analyzátor paměti JavaScriptu je k dispozici v aplikaci Visual Studio pro aplikace pro Windows Store sestavené pro Windows pomocí JavaScriptu. V tomto scénáři vytvoříte aplikaci, která nesprávně uchovává prvky modelu DOM v paměti místo odstranění prvků ve stejné sazbě, v níž jsou vytvořeny.  
  
 I když je příčina nevracení paměti v této aplikaci velmi specifická, popsané kroky ukazují pracovní postup, který je obvykle efektivní při izolaci objektů, které nevrací paměť.  
  
### <a name="running-the-javascript-memory-analyzer-test-app"></a>Spuštění testovací aplikace nástroje JavaScript Memory Analyzer  
  
1. V sadě Visual Studio vyberte **Soubor**, **Nový**, **Projekt**.  
  
2. V levém podokně zvolte **JavaScript** a pak zvolte **Windows**, **Windows 8**, pak buď **univerzální** , nebo **Windows Phone aplikace**.  
  
    > [!IMPORTANT]
    > Výsledky využití paměti uvedené v tomto tématu jsou testovány proti aplikaci systému Windows 8.  
  
3. V prostředním podokně vyberte šablonu projektu **prázdné aplikace** .  
  
4. Do pole **název** zadejte název `JS_Mem_Tester` , například a klikněte na **tlačítko OK**.  
  
5. V **Průzkumník řešení**otevřete default.html a vložte mezi značky následující kód \<body> :  
  
    ```html  
    <div class="wrapper">  
        <div id="item"></div>  
        <button class="memleak" style="display: block" >Leak Memory</button>  
    </div>  
    ```  
  
    > [!IMPORTANT]
    > Pokud používáte šablonu Windows 8.1 univerzální aplikace, je nutné aktualizovat kód HTML a CSS v obou. Okna a. Projekty WindowsPhone  
  
6. Otevřete default. CSS a přidejte následující kód CSS:  
  
    ```css  
    .memleak {  
        position: absolute; top: 100px; left: 100px;  
    }  
    ```  
  
7. Otevřete default.js a nahraďte veškerý kód tímto kódem:  
  
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
  
8. Kliknutím na klávesu F5 spusťte ladění. Ověřte, zda se na stránce zobrazuje tlačítko **nevracení paměti** .  
  
9. Přepněte zpátky na Visual Studio (ALT + TAB) a pak zvolte Shift + F5, aby se ladění zastavilo.  
  
     Teď, když jste ověřili, že aplikace funguje, můžete zkontrolovat využití paměti.  
  
### <a name="analyzing-the-memory-usage"></a>Analýza využití paměti  
  
1. Na panelu nástrojů **ladění** v seznamu **Spustit ladění** vyberte cíl ladění pro aktualizovaný projekt: jeden z emulátorů Windows Phone nebo **simulátor**.  
  
   > [!TIP]
   > V případě aplikace pro Windows Store můžete v tomto seznamu také zvolit **místní počítač** nebo **vzdálený počítač** . Výhodou použití emulátoru nebo simulátoru ale je, že ho můžete umístit do sady Visual Studio a snadno přepínat mezi spuštěnou aplikací a analyzátorem paměti JavaScriptu. Další informace najdete v tématu [spuštění aplikací ze sady Visual Studio](../debugger/run-store-apps-from-visual-studio.md) a [spuštění aplikací pro Windows Store ve vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md).  
  
2. V nabídce **ladění** vyberte možnost **Profiler výkonnosti...**.  
  
3. V **nabídce dostupné nástroje**zvolte možnost **paměť JavaScriptu**a pak zvolte možnost **Spustit**.  
  
    V tomto kurzu připojíte analyzátor paměti k spouštěnému projektu. Informace o dalších možnostech, jako je třeba připojení analyzátoru paměti k nainstalované aplikaci, najdete v tématu [paměť JavaScriptu](../profiling/javascript-memory.md).  
  
    Když spustíte analyzátor paměti, může se zobrazit řízení uživatelských účtů, které požaduje vaše oprávnění ke spuštění VsEtwCollector.exe. Vyberte **Ano**.  
  
4. V případě úspěchu vyberte tlačítko **nevracení paměti** čtyřikrát.  
  
    Když kliknete na tlačítko, kód pro zpracování událostí v default.js provede práci, která bude mít za následek nevracení paměti. Tuto informaci použijete pro účely diagnostiky.  
  
   > [!TIP]
   > Opakování scénáře, který chcete testovat při nevracení paměti, usnadňuje vyfiltrování nesouvisejících informací, například objektů přidaných do haldy při inicializaci aplikace nebo načítání stránky.  
  
5. Z běžící aplikace přepněte do sady Visual Studio (ALT + TAB).  
  
    Analyzátor paměti JavaScriptu zobrazuje informace na nové kartě v aplikaci Visual Studio.  
  
    Graf paměti v tomto souhrnném zobrazení ukazuje využití paměti procesu v čase. Zobrazení také nabízí příkazy, jako je **třeba pořídit snímek haldy**. Snímek poskytuje podrobné informace o využití paměti v určitou dobu. Další informace najdete v tématu [paměť JavaScriptu](../profiling/javascript-memory.md).  
  
6. Vyberte možnost **pořídit snímek haldy**.  
  
7. Přepněte do aplikace a vyberte možnost **nevracení paměti**.  
  
8. Přepněte do sady Visual Studio a vyberte možnost **pořídit snímek haldy** znovu.  
  
    Na tomto obrázku je znázorněný snímek směrného plánu (#1) a #2 snímků.  
  
    ![Snímek a snímek směrného plánu 2](../profiling/media/js-mem-app-snapshot2.png "JS_Mem_App_Snapshot2")  
  
   > [!NOTE]
   > Emulátor Windows Phone nezobrazuje snímek obrazovky aplikace v době pořízení snímku.  
  
9. Přepněte do aplikace a znovu klikněte na tlačítko **nevrácená paměť** .  
  
10. Přepněte do sady Visual Studio a vyberte možnost **pořídit snímek haldy** pro třetí čas.  
  
    > [!TIP]
    > Použitím třetího snímku v tomto pracovním postupu můžete odfiltrovat změny ze snímku standardních hodnot do druhého snímku, který není spojen s nevrácenou pamětí. Například je možné očekávat změny, jako je například aktualizace hlaviček a zápatí na stránce, což způsobí, že budou vygenerovány některé změny využití paměti, ale nemusí souviset s nevrácenou pamětí.  
  
     Tento obrázek ukazuje #2 snímků a #3 snímků.  
  
     ![Snímek 2 a snímek 3](../profiling/media/js-mem-app-snapshot3.png "JS_Mem_App_Snapshot3")  
  
11. V aplikaci Visual Studio klikněte na tlačítko **zastavit** a zastavte profilaci.  
  
12. V aplikaci Visual Studio Porovnejte snímky. Snímek #2 zobrazuje následující:  
  
    - Velikost haldy (zobrazená na levé straně šipky nahoru) se v porovnání s #1 snímků zvětšila o několik KB.  
  
      > [!IMPORTANT]
      > Přesné hodnoty využití paměti pro velikost haldy závisí na cíli ladění.  
  
    - Počet objektů haldy (zobrazený červenou šipkou nahoru na pravé straně) se v porovnání s #1 snímků zvýšil. Byl přidán jeden objekt (+ 1) a nebyly odebrány žádné objekty (-0).  
  
      Snímek #3 zobrazuje následující:  
  
    - Velikost haldy se znovu zvýšila o několik stovek bajtů v porovnání s #2 snímků.  
  
    - Počet objektů v haldě se znovu zvýšil v porovnání s #2 snímku. Byl přidán jeden objekt (+ 1) a nebyly odebrány žádné objekty (-0).  
  
13. V #3 snímku vyberte v pravé části text odkazu, který zobrazuje hodnotu + 1/ -0 vedle šipky pro červenou šipku nahoru.  
  
     ![Odkaz na jiné zobrazení objektů haldy](../profiling/media/js-mem-app-link.png "JS_Mem_App_Link")  
  
     Tím se otevře rozdílové zobrazení objektů v haldě, označované jako **#2 snímků #3 snímku**, ve výchozím nastavení se zobrazuje zobrazení typů. Ve výchozím nastavení se zobrazí seznam objektů přidaných do haldy mezi snímky snímků #2 a #3 snímků.  
  
14. V poli Filtr **oboru** vyberte objekty, které **zůstaly po #2 snímku**.  
  
15. Otevřete objekt HTMLDivElement v horní části stromu objektu, jak je znázorněno zde.  
  
     ![Rozdílové zobrazení počtu objektů v haldě](../profiling/media/js-mem-app-typesdiff.png "JS_Mem_App_TypesDiff")  
  
     Toto zobrazení ukazuje užitečné informace o nevracení paměti, jako je například následující:  
  
    - Toto zobrazení ukazuje element DIV s ID `item` a velikost zachovaná pro objekt je několik set bajtů (přesná hodnota se bude lišit).  
  
    - Tento objekt je objekt zbylé ze snímku #2 a představuje možnou nevrácenou paměť.  
  
      Některé znalosti aplikace v tomto okamžiku pomáhají: výběr tlačítka uvolnit **paměť** by měl odebrat element div a přidat element, takže kód nemusí fungovat správně (to znamená, že nevrací paměť). V další části se dozvíte, jak tuto chybu opravit.  
  
    > [!TIP]
    > V některých případech může být při hledání objektu ve vztahu k objektu pomoci `Global` objekt identifikovat. Provedete to tak, že otevřete místní nabídku pro identifikátor a pak zvolíte **Zobrazit v zobrazení kořene**.  
  
## <a name="fixing-the-memory-issue"></a><a name="FixingMemory"></a> Oprava potíží s pamětí  
  
1. Pomocí dat zobrazených v profileru prohlížíte kód, který je zodpovědný za odebrání elementů modelu DOM s ID "Item". K tomu dochází ve `initialize()` funkci.  
  
   ```javascript  
   function initialize() {  
  
       if (wrapper != null) {  
           elem.removeNode(true);  
       }  
   }  
   ```  
  
    `elem.removeNode(true)` pravděpodobně nepracuje správně. Prověřte, jak kód ukládá do mezipaměti prvek modelu DOM a zjistíte problém. odkaz na prvek uložený v mezipaměti není aktualizován.  
  
2. V default.js přidejte do funkce Load následující řádek kódu těsně před voláním `appendChild` :  
  
   ```javascript  
   elem = newDiv;  
   ```  
  
    Tento kód aktualizuje odkaz na prvek uložený v mezipaměti, aby byl element správně odebrán při výběru tlačítka **nevracení paměti** . Úplný kód pro funkci Load teď vypadá takto:  
  
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
  
3. V nabídce **ladění** vyberte možnost **výkon a diagnostika**.  
  
4. V **nabídce dostupné nástroje**zvolte možnost **paměť JavaScriptu**a pak zvolte možnost **Spustit**.  
  
5. Použijte stejný postup jako předtím, aby bylo možné provést tři snímky. Tady jsou shrnuté kroky:  
  
   1. V aplikaci vyberte tlačítko **nevracení paměti** čtyřikrát po sobě.  
  
   2. Přepněte do sady Visual Studio a vyberte možnost **pořídit snímek haldy** pro snímek směrného plánu.  
  
   3. V aplikaci klikněte na tlačítko **nevracení paměti** .  
  
   4. Přepněte do sady Visual Studio a vyberte možnost **pořídit snímek haldy** pro druhý snímek.  
  
   5. V aplikaci klikněte na tlačítko **nevracení paměti** .  
  
   6. Přepněte do sady Visual Studio a vyberte možnost **pořídit snímek haldy** pro třetí snímek.  
  
      Snímek #3 nyní zobrazuje velikost haldy **beze zvětšení** #2 snímku a počet objektů je + 1/ -1, což znamená, že byl přidán jeden objekt a byl odebrán jeden objekt. Toto je požadované chování.  
  
      Na následujícím obrázku vidíte #2 snímků a #3 snímků.  
  
      ![Snímky ukazující nevracení pevné paměti](../profiling/media/js-mem-app-fixed-snapshot3.png "JS_Mem_App_Fixed_Snapshot3")  
  
## <a name="see-also"></a>Viz také  
 [Paměť JavaScriptu](../profiling/javascript-memory.md)
