---
title: Zobrazení naslouchacích procesů událostí DOM | Dokumentace Microsoftu
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
- DOM events, viewing [Windows Store apps]
- event listeners, viewing [Windows Store apps]
ms.assetid: d5b679e7-87dd-4cec-9176-883db6ff0781
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1e0cf0abc35c87de3c7caa3ed00e57cb07cf987
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727382"
---
# <a name="view-dom-event-listeners"></a>Zobrazení naslouchacích procesů událostí DOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 **Události** karty Průzkumníku modelu DOM zobrazí události, které jsou spojeny s prvek modelu DOM. Každá hlavní uzel v **události** karta představuje událost, která má aktivní předplatitele. Hlavní uzel obsahuje podřízené uzly, které představují naslouchacích procesů registrované události pro konkrétní události. Kromě zobrazení naslouchacích procesů událostí, můžete použít na této kartě přejděte do umístění naslouchací proces událostí v kódu jazyka JavaScript. Informace v tomto tématu se vztahují na aplikace pro Store pomocí HTML a JavaScript.  
  
 V seznamu na **události** karta je dynamická. Pokud chcete přidat naslouchací proces událostí, když aplikace spuštěna, tam objeví nový naslouchací proces událostí. Informace o přidávání a odebírání naslouchacích procesů událostí, naleznete v tématu [tipy pro řešení problémů s naslouchacích procesů událostí](#Tips) v tomto tématu.  
  
> [!NOTE]
>  Naslouchacích procesů událostí pro prvky kódu, které nejsou prvky modelu DOM, jako například `xhr`, se nezobrazují na **události** kartu.  
  
## <a name="view-event-listeners-for-dom-elements"></a>Zobrazení naslouchacích procesů událostí prvků modelu DOM  
 Tento příklad ukazuje aplikace Windows Phone Store. Funkce Průzkumníku modelu DOM, který je zde popsáno, jsou také podporovány pro aplikace Windows Store.  
  
#### <a name="to-view-event-listeners"></a>Chcete-li zobrazit naslouchacích procesů událostí  
  
1.  V sadě Visual Studio vytvořte aplikaci JavaScript, který používá šablonu projektu aplikace Windows Phone kontingenční tabulky.  
  
2.  Šablonu otevřít v sadě Visual Studio, vyberte **emulátoru WVGA 8.1 4 v 512MB** v rozevíracím seznamu na panelu nástrojů ladění v ladicím programu:  
  
     ![Výběr cíle ladění](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")  
  
3.  Stisknutím klávesy F5 spusťte aplikaci v režimu ladění.  
  
4.  Ve spuštěné aplikaci, přejděte **3 části** položka pivotu.  
  
5.  Přepnout do sady Visual Studio (Alt + Tab nebo F12).  
  
6.  V Průzkumníku modelu DOM, zvolte `Find` v pravém horním rohu.  
  
7.  Typ `ListView`, a potom stiskněte klávesu Enter.  
  
8.  V případě potřeby vyberte **Další** tlačítko Najít `DIV` elementu, který představuje `ListView` ovládacího prvku (má tento prvek `data-win-control` hodnotu `WinJS.UI.ListView`).  
  
     `DIV` Element by měl nyní vybrat v Průzkumníku modelu DOM.  
  
9. Zvolte **události** kartu v podokně na pravé straně Průzkumníka modelu DOM.  
  
     Nyní můžete zobrazit události, které mají aktivní předplatitele `DIV` elementu, jak je znázorněno zde.  
  
     ![Události karty Průzkumníku modelu DOM](../debugger/media/js-dom-events.png "JS_DOM_Events")  
  
10. K vyhledání naslouchacích procesů událostí pro tyto události, zvolte přidružené odkazy na soubory jazyka JavaScript.  
  
11. Rychle identifikovat naslouchacích procesů událostí pro nadřazené prvky v hierarchii modelu DOM, zvolte v seznamu hierarchie v dolní části Průzkumníku modelu DOM nadřazeného elementu.  
  
     ![Výběr nadřazené prvky v modelu DOM hierarchie](../debugger/media/js-dom-breadcrumbs.png "JS_DOM_Breadcrumbs")  
  
     **Události** karta zobrazuje naslouchacích procesů událostí pro libovolný element, který jste vybrali v seznamu hierarchie.  
  
###  <a name="Tips"></a> Tipy pro řešení problémů s naslouchacích procesů událostí  
 V některých scénářích aplikace naslouchacích procesů událostí musí být explicitně odebrány [removeEventListener](http://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx). Použití **události** kartu v Průzkumníku modelu DOM, který chcete otestovat, jestli naslouchacích procesů událostí byly odebrány z modelu DOM prvků za běhu programu. Zde jsou některé tipy pro řešení těchto typů problémů:  
  
-   Pro aplikace, které používají model navigace jednostránkové implementované v sadě Visual Studio [šablony projektů](http://msdn.microsoft.com/library/windows/apps/hh758331.aspx), není obvykle nutné odebrat naslouchacích procesů událostí zaregistrované u objektů, jako jsou například prvky modelu DOM, které jsou součástí na stránce. V tomto scénáři prvek modelu DOM a jeho přidružené události naslouchací procesy mají stejnou životnost a mohou být uvolněna.  
  
-   Pokud se liší od naslouchací proces související události životního cyklu od prvku modelu DOM nebo objektu, budete muset volat `removeEventListener` metody. Například, pokud použijete `window.onresize` událost, možná budete muset odebrat naslouchací proces událostí, jestliže opustíte na stránce, kde zpracování události.  
  
-   Pokud `removeEventListener` nepodaří odeberte zadaný naslouchací proces by může být získání volána na jinou instanci objektu. Můžete použít [bind – metoda (Function)](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/bind-method-function-javascript.md) metoda k vyřešení tohoto problému, když přidáte naslouchací proces.  
  
-   Chcete-li odebrat naslouchací proces událostí, která byla přidána pomocí [bind – metoda (Function)](~/E:/Repos/visualstudio-docs-pr/scripting-docs/javascript/reference/bind-method-function-javascript.md) nebo pomocí anonymní funkce uložit instance funkci tehdy, když přidejte naslouchací proces. Tady je jeden způsob, jak bezpečně tento model použijte:  
  
    ```javascript  
    // You could use the following code within the constructor function of an object, or  
    // in the ready function of a PageControl object (Store app).  
    this.storedHandler = this._handlerFunc.bind(this);  
    elem.addEventListener('mouseup', this.storedHandler);  
  
    // In this example, add the following code in the PageControl object's unload function.  
    elem.removeEventListener('mouseup', this.storedHandler);  
  
    ```  
  
     Pokud pomocí následujícího kódu místo uložení odkazu na vázanou funkci, nebude možné explicitně odstranit naslouchací proces událostí:  
  
    ```javascript  
    // Avoid this pattern. No reference to the bound function is available.  
    elem.addEventListener('mouseup', this._handlerFunc.bind(this));  
    ```  
  
-   Naslouchací proces událostí nelze odebrat pomocí `removeEventListener` Pokud jste přidali pomocí `obj.on<eventname>` atribut, například `window.onresize = handlerFunc`.  
  
-   Použijte analýzu paměti jazyka JavaScript do [paměti jazyka JavaScript](../profiling/javascript-memory.md) ve vaší aplikaci. Naslouchacích procesů událostí, které musí být explicitně odebrat může zobrazit jako nenavrácení paměti.  
  
## <a name="see-also"></a>Viz také  
 [Rychlý start: Ladění kódu HTML a CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Ladění stylů CSS pomocí Průzkumníka modelu DOM](../debugger/debug-css-styles-using-dom-explorer.md)   
 [Ladění rozložení pomocí průzkumníka modelu DOM](../debugger/debug-layout-using-dom-explorer.md)



