---
title: 'Návod: Zvýšení rychlosti odezvy uživatelského rozhraní (HTML) | Dokumentace Microsoftu'
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
- performance tools, JavaScript [Store apps]
- performance, JavaScript [Store apps]
- performance, HTML [Store apps]
- performance tools, HTML [Store apps]
ms.assetid: 7e5a2524-dbf5-4a40-b5d6-2d1ed7fff3de
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0cf1b080a0e803beda6682265dc383dc43a33d0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791138"
---
# <a name="walkthrough-improving-ui-responsiveness-html"></a>Návod: Zvýšení rychlosti odezvy uživatelského rozhraní (HTML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento názorný postup vás provede procesem identifikace a řešení potíží s výkonem s použitím [profiler odezvy uživatelského rozhraní HTML](../profiling/html-ui-responsiveness.md). Profiler je k dispozici v aplikacích Visual Studio pro Windows Universal a Windows Store pomocí jazyka JavaScript. V tomto scénáři vytvoříte aplikace pro testy výkonu, která aktualizuje elementů modelu DOM příliš často a využívat profiler a identifikovat a opravit tento problém.  
  
### <a name="creating-and-running-the-performance-test-app"></a>Vytváření a spouštění výkon testování aplikace  
  
1.  V sadě Visual Studio vytvořte nový projekt univerzální JavaScript Windows. (Vyberte **soubor / nový / Project**. Zvolte **JavaScript** v levém podokně a pak zvolte **Windows**, **Windows 10**, pak buď **univerzální**, nebo  **Windows Phone**.  
  
2.  > [!IMPORTANT]
    >  Aplikace pro Windows 8 se zobrazí výsledky diagnostiky, které jsou uvedené v tomto tématu.  
  
3.  Zvolte jednu z prázdného projektu šablon v prostředním podokně, jako například **prázdnou aplikaci**.  
  
4.  V **název** zadejte název, jako `JS_Perf_Tester`a klikněte na tlačítko **OK**.  
  
5.  V **Průzkumníka řešení**, otevřete soubor default.html a vložte následující kód mezi \<text > značky:  
  
    ```html  
    <div class="wrapper">  
        <button id="content">Waiting for values</button>  
    </div>  
    ```  
  
6.  Otevřete default.css a přidejte následující kód šablony stylů CSS:  
  
    ```css  
    #content {  
        margin-left: 100px;  
        margin-top: 100px;  
    }  
    ```  
  
7.  Otevřete default.js a nahraďte celý kód s tímto kódem:  
  
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
  
8.  Stisknutím klávesy F5 spusťte ladění. Ověřte, že **čekání na hodnoty** tlačítko se zobrazí na stránce.  
  
9. Zvolte **čekání na hodnoty** a ověřit, tlačítko text a barvu aktualizovat přibližně jednou za sekundu. Jedná se o účel.  
  
10. Přepněte zpět do sady Visual Studio (Alt + Tab) a klikněte na tlačítko Shift + F5 ukončete ladění.  
  
     Teď, když jste ověřili, že aplikace funguje, můžete zkontrolovat svůj výkon pomocí profileru.  
  
### <a name="analyzing-performance-data"></a>Analýza údajů o výkonu  
  
1. Na **ladění** nástrojů v **spustit ladění** seznamu, vyberte jednu z emulátory Windows Phone nebo **simulátor**.  
  
2. Na **ladění** nabídce zvolte **výkon a Diagnostika**.  
  
3. V **dostupných nástrojů**, zvolte **rychlosti odezvy uživatelského rozhraní HTML**a klikněte na tlačítko **Start**.  
  
    V tomto kurzu budete se připojuje se profiler na spouštěný projekt. Informace o další možnosti, jako je připojení profileru k nainstalované aplikace, najdete v části [rychlost odezvy HTML UI](../profiling/html-ui-responsiveness.md).  
  
    Při spuštění profileru, může se zobrazit řízení uživatelských účtů, ke spuštění VsEtwCollector.exe. Zvolte **Ano**.  
  
4. Ve spuštěné aplikaci vyberte **čekání na hodnoty** a počkejte asi 10 sekund. Ověřte, že tlačítko text a barvu aktualizovat přibližně jednou za sekundu.  
  
5. Ze spuštěné aplikaci přepněte do sady Visual Studio (Alt + Tab).  
  
6. Zvolte **zastavit shromažďování**.  
  
    Profiler informace zobrazí na nové kartě v sadě Visual Studio. Když se podíváte na využití procesoru a vizuální propustnost (FPS) dat, mohli snadno identifikovat trendy několik:  
  
   - Zvýší využití procesoru výrazně po přibližně 3 sekund (při stisknutí **čekání na hodnoty** tlačítko) a zobrazuje vymazat vzor událostí (konzistentní kombinaci skriptování, stylu a události vykreslování) od této chvíle v.  
  
   - Vizuální propustnost není ovlivněná a snímků za Sekundu zůstává na 60 v průběhu (to znamená, nejsou žádné vynechaných rámce).  
  
     Podívejme se na část typický graf využití procesoru a zjistěte, co aplikace dělá v tomto období vysoké aktivity.  
  
7. Vyberte druhou část jedné až dvou uprostřed graf využití procesoru (buď kliknutím a přetažením nebo pomocí kláves tab a šipka). Následující obrázek znázorňuje graf využití procesoru po provedení výběru. Nesdílené oblast je výběr.  
  
    ![Graf využití procesoru](../profiling/media/js-htmlviz-app-cpu.png "JS_HTMLViz_App_CPU")  
  
8. Zvolte **přiblížit**.  
  
    Grafu se změní a zobrazí vybrané období podrobněji. Následující obrázek znázorňuje graf využití procesoru po přiblížit. (Konkrétní data se můžou lišit, ale bude obecný vzor zřejmý.)  
  
    ![V zobrazení v měřítku](../profiling/media/js-htmlviz-app-zoom.png "JS_HTMLViz_App_Zoom")  
  
    Podrobnosti časové osy ve spodní části podokna ukazuje příklad podrobnosti pro vybrané období.  
  
    ![Podrobnosti časové osy](../profiling/media/js-htmlviz-app-details.png "JS_HTMLViz_App_Details")  
  
    Události v časové ose podrobnosti potvrzení viditelné trendy v graf využití procesoru: obsahuje mnoho událostí probíhat přes krátkou dobu. Zobrazení podrobností časová osa ukazuje, že tyto události jsou `Timer`, `Layout`, a `Paint` události.  
  
9. Pomocí místní nabídky (nebo kliknutím pravým tlačítkem) mezi `Timer` událostí ve spodní části podokna a zvolte **filtru na události**. Následující obrázek znázorňuje příklad podrobnosti typické pro jeden z `Timer` události v této aplikaci test.  
  
     ![Událost časovače](../profiling/media/js-htmlviz-app-timer.png "JS_HTMLViz_App_Timer")  
  
     Širokou škálu faktů mohou úsporách získaných data. Příklad:  
  
    -   Každý `Timer` události barevné označení k jeho identifikaci jako skriptovací událostí obsahuje volání `document.createElement`následovaný výpočet stylu a volání `style.backgroundColor` a `appendChild()`.  
  
    -   V krátkém časovém úseku, v vybrané (přibližně 1 až 2 sekund), existuje velký počet `Timer`, `Layout`, a `Paint` události probíhat. `Timer` Daleko častěji než jednu aktualizaci za sekundu, které je viditelně zřejmý po spuštění aplikace a zvolte dojde k událostem **čekání na hodnoty** tlačítko.  
  
10. K prozkoumání, zvolte odkaz pro anonymní funkce pro jeden z `Timer` události v dolním levém podokně. Otevře se v souboru default.js následující funkce:  
  
    ```javascript  
    function update() {  
  
        setTimeout(function () {  
  
            setValues();  
            if (count < max) { update(); }  
        });  
    }  
    ```  
  
     Tato rekurzivní funkce nastaví smyčku, která volá `setValues()` funkce, která aktualizuje tlačítko v uživatelském rozhraní. Zkoumání různých časovače událostí v profileru, zjistíte, že nejvíce nebo všechny události časovače výsledkem tento kód, který je spuštěn příliš často, aby se zobrazovalo pravděpodobně zde vznikl problém.  
  
### <a name="fixing-the-performance-issue"></a>Oprava potíží s výkonem  
  
1.  Nahradit `update()` funkce s následujícím kódem:  
  
    ```javascript  
    function update() {  
  
        setTimeout(function () {  
  
            setValues();  
            if (count < max) { update(); }  
        }, 1000 );  
    }  
    ```  
  
     Tuto opravenou verzi kódu zahrnuje 1000 prodlevě milisekund bylo vynecháno z předchozí verze kódu, takže použijte výchozí hodnotu zpoždění. Z dat profileru, zobrazí se, že výchozí hodnota je nula milisekund, které způsobily `setValues()` funkce pro spuštění příliš často.  
  
2.  Znovu spustit profiler odezvy uživatelského rozhraní HTML a zkontrolujte graf využití procesoru. Zjistíte, že jsou pryč nadměrné události a využití procesoru zamítl k téměř nulové. Napravila.  
  
## <a name="see-also"></a>Viz také  
 [Rychlost odezvy uživatelského rozhraní HTML](../profiling/html-ui-responsiveness.md)



