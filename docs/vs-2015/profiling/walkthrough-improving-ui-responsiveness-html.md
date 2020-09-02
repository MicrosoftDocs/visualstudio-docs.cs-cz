---
title: 'Návod: vylepšení odezvy uživatelského rozhraní (HTML) | Microsoft Docs'
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
- performance tools, JavaScript [Store apps]
- performance, JavaScript [Store apps]
- performance, HTML [Store apps]
- performance tools, HTML [Store apps]
ms.assetid: 7e5a2524-dbf5-4a40-b5d6-2d1ed7fff3de
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7224dc1ddcffc203c930a3ead01c2f541af2122f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64792878"
---
# <a name="walkthrough-improving-ui-responsiveness-html"></a>Návod: Zvýšení rychlosti odezvy uživatelského rozhraní (HTML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod vás provede procesem identifikace a řešení potíží s výkonem pomocí [profileru rychlost odezvy v uživatelském rozhraní HTML](../profiling/html-ui-responsiveness.md). Profiler je k dispozici v aplikaci Visual Studio pro univerzální aplikace pro Windows a aplikace pro Windows Store pomocí JavaScriptu. V tomto scénáři vytvoříte aplikaci testu výkonu, která aktualizuje prvky modelu DOM příliš často a pomocí profileru tento problém identifikujte a opravíte.  
  
### <a name="creating-and-running-the-performance-test-app"></a>Vytvoření a spuštění aplikace test výkonnosti  
  
1. V aplikaci Visual Studio vytvořte nový projekt Windows Universal JavaScript. (Vyberte **soubor/nový/projekt**. V levém podokně zvolte **JavaScript** a pak zvolte **Windows**, **Windows 10**, pak buď **Universal**, nebo **Windows Phone**.  
  
2. > [!IMPORTANT]
    > Diagnostické výsledky uvedené v tomto tématu se zobrazí pro aplikaci systému Windows 8.  
  
3. V prostředním podokně vyberte jednu z prázdných šablon projektů, jako je například **prázdná aplikace**.  
  
4. Do pole **název** zadejte název `JS_Perf_Tester` , například a klikněte na **tlačítko OK**.  
  
5. V **Průzkumník řešení**otevřete default.html a vložte mezi značky následující kód \<body> :  
  
    ```html  
    <div class="wrapper">  
        <button id="content">Waiting for values</button>  
    </div>  
    ```  
  
6. Otevřete default. CSS a přidejte následující kód CSS:  
  
    ```css  
    #content {  
        margin-left: 100px;  
        margin-top: 100px;  
    }  
    ```  
  
7. Otevřete default.js a nahraďte veškerý kód tímto kódem:  
  
    ```javascript  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var activation = Windows.ApplicationModel.Activation;  
  
        var content;  
        var wrapper;  
  
        app.onactivated = function (args) {  
            if (args.detail.kind === activation.ActivationKind.launch) {  
                if (args.detail.previousExecutionState !== activation.ApplicationExecutionState.terminated) {  
  
                    content = document.getElementById("content");  
                    wrapper = document.querySelector(".wrapper");  
  
                    content.addEventListener("click", handler);  
  
                } else {  
                }  
  
                args.setPromise(WinJS.UI.processAll());  
            }  
        };  
  
        app.oncheckpoint = function (args) {  
        };  
  
        app.start();  
  
        var idx = 0;  
        var count = 0;  
        var max = 5000;  
        var text = ["what", "is", "the", "Matrix?"];  
        var color = ["red", "crimson", "maroon", "purple"];  
  
        function increment() {  
  
            setTimeout(function () {  
  
                idx++;  
                count++;  
  
                if (idx > 3) { idx = 0; }  
                if (count < max) { increment(); }  
  
            }, 1000);  
        }  
  
        function setValues() {  
  
            content = document.getElementById("content");  
            content.removeNode(true);  
  
            var newNode = document.createElement("button");  
            newNode.id = "content";  
            newNode.textContent = text[idx];  
            //newNode.textContent = getData();  
            newNode.style.backgroundColor = color[idx];  
            //newNode.style.animationName = "move";  
            //count++;  
  
            wrapper.appendChild(newNode);  
  
        }  
  
        function update() {  
  
            setTimeout(function () {  
  
                setValues();  
                if (count < max) { update(); }  
            });  
        }  
  
        function handler(args) {  
  
            content.textContent = "eenie";  
            increment();  
            update();  
        }  
  
    })();  
  
    ```  
  
8. Kliknutím na klávesu F5 spusťte ladění. Ověřte, že se na stránce zobrazuje tlačítko **čekat na hodnoty** .  
  
9. Vyberte možnost **čekat na hodnoty** a ověřte, zda se text a barva tlačítka aktualizují přibližně jednou za sekundu. Toto chování je úmyslné.  
  
10. Přepněte zpátky na Visual Studio (ALT + TAB) a pak zvolte Shift + F5, aby se ladění zastavilo.  
  
     Teď, když jste ověřili, že aplikace funguje, můžete zkontrolovat její výkon pomocí profileru.  
  
### <a name="analyzing-performance-data"></a>Analýza údajů o výkonu  
  
1. Na panelu nástrojů **ladění** v seznamu **Spustit ladění** vyberte jeden z Windows Phone emulátory nebo **simulátor**.  
  
2. V nabídce **ladění** vyberte možnost **výkon a diagnostika**.  
  
3. V **nabídce dostupné nástroje**zvolte **rychlost odezvy uživatelského rozhraní HTML**a pak zvolte **Spustit**.  
  
    V tomto kurzu připojíte profiler k projektu po spuštění. Informace o dalších možnostech, jako je připojení profileru k nainstalované aplikaci, najdete v tématu [odezva uživatelského rozhraní HTML](../profiling/html-ui-responsiveness.md).  
  
    Když spustíte Profiler, může se zobrazit řízení uživatelských účtů, které požaduje vaše oprávnění ke spuštění VsEtwCollector.exe. Vyberte **Ano**.  
  
4. Ve spuštěné aplikaci vyberte možnost **čekat na hodnoty** a počkejte asi 10 sekund. Ověřte, zda se text a barva tlačítka aktualizují přibližně jednou za sekundu.  
  
5. Z běžící aplikace přepněte do sady Visual Studio (ALT + TAB).  
  
6. Vyberte **Zastavit shromažďování**.  
  
    Profiler zobrazuje informace na nové kartě v aplikaci Visual Studio. Když se podíváte na využití procesoru a data pro vizuální propustnost (FPS), můžete snadno identifikovat několik trendů:  
  
   - Využití procesoru se výrazně zvyšuje po 3 sekundách (po stisknutí tlačítka **čekání na hodnoty** ) a zobrazuje jasný vzor událostí (konzistentní kombinace skriptování, stylů a vykreslování událostí) od tohoto okamžiku.  
  
   - Propustnost vizuálů není ovlivněná a FPS zůstává v 60 (to znamená, že neexistují žádné vynechané snímky).  
  
     Pojďme se podívat na typickou část grafu využití CPU, kde zjistíte, co aplikace dělá v tomto období vysoké aktivity.  
  
7. V grafu využití procesoru vyberte druhou část 1:2 (klikněte na a přetáhněte nebo použijte kartu a klávesy se šipkami). Následující ilustrace znázorňuje graf využití procesoru po provedení výběru. Oblast, která není sdílená, je výběr.  
  
    ![Graf využití procesoru](../profiling/media/js-htmlviz-app-cpu.png "JS_HTMLViz_App_CPU")  
  
8. Vyberte možnost **přiblížit**.  
  
    Graf se změní tak, aby zobrazoval vybrané období podrobněji. Následující ilustrace znázorňuje graf využití procesoru po přiblížení. (Konkrétní data se mohou lišit, ale obecný vzor bude zřejmý.)  
  
    ![Přiblížení zobrazení](../profiling/media/js-htmlviz-app-zoom.png "JS_HTMLViz_App_Zoom")  
  
    Podrobnosti časové osy v dolním podokně zobrazují příklad podrobností pro vybrané období.  
  
    ![Podrobnosti časové osy](../profiling/media/js-htmlviz-app-details.png "JS_HTMLViz_App_Details")  
  
    Události v podrobnostech časové osy potvrzují viditelné trendy v grafu využití CPU: během krátkých časových úseků dochází k mnoha událostem. Zobrazení Podrobnosti časové osy ukazuje, že se jedná o události `Timer` , `Layout` a `Paint` .  
  
9. V dolním podokně použijte kontextovou nabídku (nebo klikněte pravým tlačítkem myši) na jednu z `Timer` událostí a vyberte možnost **filtrovat na událost**. Následující ilustrace znázorňuje příklad podrobností typických pro jednu z `Timer` událostí v této testovací aplikaci.  
  
     ![Událost časovače](../profiling/media/js-htmlviz-app-timer.png "JS_HTMLViz_App_Timer")  
  
     Z dat může být mohli celá řada skutečností. Příklad:  
  
    - Jednotlivé `Timer` události, barevně kódované k identifikaci jako událost skriptování, obsahuje volání `document.createElement` , následované výpočtem stylu a volání `style.backgroundColor` a `appendChild()` .  
  
    - Ve vybraném krátkém časovém intervalu (přibližně jedna až 2 sekundy) je k dispozici velký počet `Timer` `Layout` událostí, a `Paint` . `Timer`Události nastávají mnohem častěji než jedna aktualizace za sekundu, která je viditelně zřejmá po spuštění aplikace a kliknutí na tlačítko **čekání na hodnoty** .  
  
10. Pro prošetření klikněte na odkaz anonymní funkce pro jednu z `Timer` událostí v levém dolním podokně. V default.js se otevře následující funkce:  
  
    ```javascript  
    function update() {  
  
        setTimeout(function () {  
  
            setValues();  
            if (count < max) { update(); }  
        });  
    }  
    ```  
  
     Tato rekurzivní funkce nastaví smyčku, která volá `setValues()` funkci, která aktualizuje tlačítko v uživatelském rozhraní. Prozkoumáním různých událostí časovače v profileru zjistíte, že většina nebo všechny události časovače vyplývají z tohoto kódu, který běží příliš často, takže se zdá, že tento problém pochází.  
  
### <a name="fixing-the-performance-issue"></a>Oprava potíží s výkonem  
  
1. Nahraďte `update()` funkci následujícím kódem:  
  
    ```javascript  
    function update() {  
  
        setTimeout(function () {  
  
            setValues();  
            if (count < max) { update(); }  
        }, 1000 );  
    }  
    ```  
  
     Tato pevná verze kódu zahrnuje zpoždění 1000 milisekund, které bylo vynecháno z předchozí verze kódu, což má za následek použití výchozí hodnoty zpoždění. Z dat profileru se zdá, že výchozí hodnota je nula milisekund, což způsobilo, že se `setValues()` funkce spouštěla příliš často.  
  
2. Znovu spusťte Profiler odezvy uživatelského rozhraní HTML a podívejte se na graf využití procesoru. Zjistíte, že dojde k výpadku nadměrných událostí a využití procesoru se snížilo na nulu. Určí!  
  
## <a name="see-also"></a>Viz také  
 [Rychlost odezvy uživatelského rozhraní (HTML)](../profiling/html-ui-responsiveness.md)
