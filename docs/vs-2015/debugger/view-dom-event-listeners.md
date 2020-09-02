---
title: Zobrazit naslouchací procesy událostí modelu DOM | Microsoft Docs
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
- DOM events, viewing [Windows Store apps]
- event listeners, viewing [Windows Store apps]
ms.assetid: d5b679e7-87dd-4cec-9176-883db6ff0781
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 64d4892080aaf0cf04e4b208b1a0bdb7a7a4480d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65693573"
---
# <a name="view-dom-event-listeners"></a>Zobrazení naslouchacích procesů událostí DOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Karta **události** v Průzkumníkovi modelu DOM zobrazuje události, které jsou přidruženy k elementu modelu DOM. Každý nejvyšší uzel na kartě **události** představuje událost, která má aktivní předplatitele. Nejvyšší uzel obsahuje poduzly, které reprezentují naslouchací procesy registrovaných událostí pro konkrétní událost. Kromě zobrazení posluchačů událostí můžete pomocí této karty přejít do umístění naslouchacího procesu události v kódu JavaScriptu. Informace v tomto tématu se vztahují na aplikace pro Store s použitím HTML a JavaScriptu.

 Seznam na kartě **události** je dynamický. Pokud přidáte naslouchací proces události, když je aplikace spuštěná, zobrazí se zde nový naslouchací proces událostí. Informace o přidávání a odebírání posluchačů událostí najdete v tématu [tipy pro řešení problémů s naslouchacími procesy událostí](#Tips) v tomto tématu.

> [!NOTE]
> Naslouchací procesy událostí pro prvky kódu, které nejsou prvky modelu DOM, například `xhr` , se nezobrazují na kartě **události** .

## <a name="view-event-listeners-for-dom-elements"></a>Zobrazení naslouchacího procesu událostí pro elementy DOM
 Tento příklad ukazuje aplikaci Windows Phone Store. Funkce Průzkumníka modelu DOM popsané tady jsou podporované i pro aplikace pro Windows Store.

#### <a name="to-view-event-listeners"></a>Zobrazení posluchačů událostí

1. V aplikaci Visual Studio vytvořte aplikaci JavaScriptu, která používá šablonu projektu Windows Phone aplikace Pivot.

2. Když je šablona otevřená v sadě Visual Studio, vyberte v rozevíracím seznamu na panelu nástrojů ladění v ladicím programu možnost **emulátor 8,1 WVGA 4IN 512 MB** :

     ![Výběr cíle ladění](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")

3. Stisknutím klávesy F5 spusťte aplikaci v režimu ladění.

4. Ve spuštěné aplikaci přejít na **oddíl 3** položka pivotu.

5. Přepněte do sady Visual Studio (ALT + TAB nebo F12).

6. V Průzkumníku modelu DOM vyberte `Find` v pravém horním rohu.

7. Zadejte `ListView` a potom stiskněte klávesu ENTER.

8. V případě potřeby klikněte na tlačítko **Další** a vyhledejte `DIV` prvek, který představuje `ListView` ovládací prvek (Tento prvek má `data-win-control` hodnotu `WinJS.UI.ListView` ).

     `DIV`Element by měl být nyní vybrán v Průzkumníku modelu DOM.

9. V podokně na pravé straně Průzkumníka modelu DOM vyberte kartu **události** .

     Nyní můžete zobrazit události, které mají aktivní předplatitele `DIV` prvku, jak je znázorněno zde.

     ![Karta události v Průzkumníkovi modelu DOM](../debugger/media/js-dom-events.png "JS_DOM_Events")

10. Chcete-li vyhledat naslouchací procesy událostí pro tyto události, vyberte přidružené odkazy na soubory JavaScriptu.

11. Chcete-li rychle identifikovat naslouchací procesy událostí pro nadřazené elementy v hierarchii modelu DOM, vyberte nadřazený prvek v seznamu hierarchie v dolní části Průzkumníka modelu DOM.

     ![Výběr nadřazených elementů v hierarchii modelu DOM](../debugger/media/js-dom-breadcrumbs.png "JS_DOM_Breadcrumbs")

     Karta **události** zobrazuje naslouchací procesy událostí pro libovolný prvek, který vyberete v seznamu hierarchie.

### <a name="tips-for-resolving-issues-with-event-listeners"></a><a name="Tips"></a> Tipy pro řešení problémů s naslouchacími procesy událostí
 V některých scénářích aplikací musí být naslouchací procesy událostí explicitně odebrány pomocí [removeEventListener](https://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx). Použijte kartu **události** v Průzkumníku modelu DOM k otestování, zda byly při spuštění kódu z prvků modelu DOM odebrány události naslouchací proces událostí. Zde jsou některé tipy, které vám pomohou vyřešit tyto typy problémů:

- Pro aplikace, které používají navigační model s jednou stránkou implementované v [šablonách projektů](https://msdn.microsoft.com/library/windows/apps/hh758331.aspx)sady Visual Studio, není obvykle nutné odebrat naslouchací procesy pro události registrované pro objekty, jako jsou například prvky modelu DOM, které jsou součástí stránky. V tomto scénáři má element DOM a přidružené naslouchací procesy událostí stejnou životnost a může být uvolněna z paměti.

- Pokud je doba života elementu nebo objektu modelu DOM odlišná od přidruženého naslouchacího procesu události, může být nutné zavolat `removeEventListener` metodu. Například pokud použijete `window.onresize` událost, může být nutné odebrat naslouchací proces události, Pokud opustíte stránku, na kterou událost zpracováváte.

- Pokud `removeEventListener` se nepovede odebrat zadaný naslouchací proces, může se volat na jinou instanci objektu. Můžete použít metodu [Bind metody (Function)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) k vyřešení tohoto problému při přidávání naslouchacího procesu.

- Chcete-li odebrat naslouchací proces událostí, který byl přidán buď pomocí [metody bind (Function)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) , nebo pomocí anonymní funkce, uložte instanci funkce při přidání naslouchacího procesu. Tady je jeden ze způsobů, jak tento model bezpečně použít:

    ```javascript
    // You could use the following code within the constructor function of an object, or
    // in the ready function of a PageControl object (Store app).
    this.storedHandler = this._handlerFunc.bind(this);
    elem.addEventListener('mouseup', this.storedHandler);

    // In this example, add the following code in the PageControl object's unload function.
    elem.removeEventListener('mouseup', this.storedHandler);

    ```

     Použijete-li následující kód místo uložení odkazu na vázanou funkci, nebudete moci naslouchací proces události odebrat explicitně:

    ```javascript
    // Avoid this pattern. No reference to the bound function is available.
    elem.addEventListener('mouseup', this._handlerFunc.bind(this));
    ```

- Naslouchací proces událostí nejde odebrat pomocí `removeEventListener` , pokud jste ho přidali pomocí atributu, jako je například `obj.on<eventname>` `window.onresize = handlerFunc` .

- Použijte nástroj JavaScript Memory Analyzer pro [javascriptovou paměť](../profiling/javascript-memory.md) ve vaší aplikaci. Naslouchací procesy událostí, které je nutné explicitně odebrat, se mohou zobrazit jako nevracení paměti.

## <a name="see-also"></a>Viz také

- [Rychlý start: Ladění kódu HTML a CSS](../debugger/quickstart-debug-html-and-css.md)
- [Ladění stylů CSS pomocí průzkumníka modelu DOM](../debugger/debug-css-styles-using-dom-explorer.md)
- [Ladění rozložení pomocí průzkumníka modelu DOM](../debugger/debug-layout-using-dom-explorer.md)