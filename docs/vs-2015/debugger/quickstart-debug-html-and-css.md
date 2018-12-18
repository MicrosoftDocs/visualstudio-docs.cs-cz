---
title: 'Rychlý start: Ladění kódu HTML a CSS | Dokumentace Microsoftu'
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
- VS.WebClient.DomExplorer
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, CSS
- debugging, HTML
- debugging, JavaScript [Windows Store apps]
- DOM Explorer [Windows Store apps]
ms.assetid: 6d156cff-36c6-425a-acf8-e1f02d4f7869
caps.latest.revision: 104
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 710bafe2383d95358ba06a287a300d9aea7baf66
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729979"
---
# <a name="quickstart-debug-html-and-css"></a>Rychlý start: Ladění kódu HTML a CSS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Pro aplikace JavaScript Visual Studio poskytuje komplexní možnosti ladění, který obsahuje funkce, které jsou pro vývojáře v aplikaci Internet Explorer a Visual Studio srozumitelná. Tyto funkce jsou podporovány pro [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)], aplikace pro Windows Phone Store a pro aplikace vytvořené pomocí nástrojů Visual Studio pro Apache Cordova  
  
 Interaktivní ladění modelu k dispozici prostřednictvím nástrojů kontroly modelu DOM můžete zobrazit a upravit vykresleným kódem HTML a CSS. Provedete to vše bez zastavení a restartování ladicího programu.  
  
 V tomto tématu:  
  
- [Kontrola live DOM](#InspectingDOM)  
  
- [Výběr elementů](#SelectingElements)  
  
  Další informace o použití Průzkumníka modelu DOM naleznete v následujících tématech:  
  
- [Ladění stylů CSS pomocí průzkumníka modelu DOM](../debugger/debug-css-styles-using-dom-explorer.md)  
  
- [Ladění rozložení pomocí průzkumníka modelu DOM](../debugger/debug-layout-using-dom-explorer.md)  
  
- [Zobrazení naslouchacích procesů událostí DOM](../debugger/view-dom-event-listeners.md)  
  
- [Aktualizace aplikace (JavaScript)](../debugger/refresh-an-app-javascript.md)  
  
- [Ladění ovládacího prvku WebView](../debugger/debug-a-webview-control.md)  
  
  Informace o dalších funkcí, jako je například používání okna konzoly jazyka JavaScript a nastavovat zarážky, ladění jazyka JavaScript naleznete v tématu [rychlý start: ladění JavaScriptu](../debugger/quickstart-debug-javascript-using-the-console.md) a [ladění aplikací v sadě Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
##  <a name="InspectingDOM"></a> Kontrola live DOM  
 Průzkumník modelu DOM se dozvíte, zobrazení vykreslené stránky a Průzkumníka modelu DOM můžete změnit hodnoty a hned vidět výsledky. To umožňuje testovat změny bez zastavení a restartování ladicího programu. Zdrojový kód v projektu nemění, když pracujete s stránce tímto způsobem, takže když najdete odpovídající kód opravy provedete změny zdrojového kódu.  
  
> [!TIP]
>  Aby se zabránilo zastavení a restartování ladicího programu, když provedete změny zdrojového kódu, můžete aktualizovat aplikace pomocí **aktualizovat Windows app** tlačítko na panelu nástrojů ladění (nebo stisknutím klávesy F4). Další informace najdete v tématu [aktualizace aplikace (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
 Můžete použít Průzkumníka modelu DOM do:  
  
- Vyhledejte podstrom prvek modelu DOM a zkontrolujte vykresleným kódem HTML, CSS a JavaScriptu.  
  
- Dynamicky upravit atributy a stylů CSS pro elementy vykreslované a hned vidět výsledky.  
  
- Zkontrolujte použití stylů CSS pro elementy stránek a trasování, které se použily pravidla.  
  
  Při ladění aplikací často potřebujete k výběru elementů v Průzkumníku modelu DOM. Při výběru prvku hodnoty zobrazené na kartách na pravé straně Průzkumníka modelu DOM automaticky aktualizovat tak, aby odrážely vybraný element v Průzkumníku modelu DOM. Jedná se o karty: **styly**, **vypočítané**, **rozložení**. Windows Store apps podporuje také **události** a **změny** karty. Další informace o výběru elementů naleznete v tématu [výběru elementů](#SelectingElements).  
  
> [!TIP]
>  Pokud se zavře okno Průzkumníka modelu DOM, zvolte **ladění**>**Windows** > **Průzkumníka modelu DOM** znovu otevřít. V okně se zobrazí jenom při relaci ladění skriptu.  
  
 V postupu, který následuje přejdeme procesem interaktivně pomocí Průzkumníka modelu DOM ladění aplikace. Vytvoříme aplikaci, která bude `FlipView` ovládací prvek a pak ho ladit. Aplikace obsahuje několik chyb.  
  
> [!WARNING]
>  Následující ukázkové aplikace je aplikace Windows Store. Stejné funkce jsou podporované pro Cordova, ale aplikace bude odlišná.  
  
#### <a name="to-debug-by-inspecting-the-live-dom"></a>Chcete-li ladit zkontrolováním live DOM  
  
1. Vytvoření nového řešení v sadě Visual Studio výběrem **souboru** > **nový projekt**.  
  
2. Zvolte **JavaScript** > **Store**, zvolte buď **aplikací Windows** nebo **aplikace Windows Phone**a klikněte na tlačítko  **Prázdná aplikace**.  
  
3. Zadejte název projektu, například `FlipViewApp`a zvolte **OK** vytvořte aplikaci.  
  
4. V elementu tělo default.html přidejte tento kód:  
  
   ```html  
   <div id="flipTemplate" data-win-control="WinJS.Binding.Template"  
            style="display:none">  
       <div class="fixedItem" >  
           <img src="#" data-win-bind="src: flipImg" />  
       </div>  
   </div>  
   <div id="fView" style="width:100px;height:100px"  
       data-win-control="WinJS.UI.FlipView" data-win-options="{  
       itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">  
   </div>  
   ```  
  
5. Otevřete default.css a přidejte následující šablony stylů CSS:  
  
   ```css  
   #fView {  
       background-color:#0094ff;  
       height: 100%;  
       width: 100%;  
       margin: 25%;  
   }  
   ```  
  
6. Nahraďte kód v souboru default.js s tímto kódem:  
  
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
  
           pages.setAt(0, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223195" });  
           pages.setAt(1, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223196" });  
           pages.setAt(2, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
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
  
    Následující obrázek znázorňuje, co chceme vidět, pokud jsme tuto aplikaci spustit v emulátoru telefonu (vypadá podobně jako v simulátoru). Ale pokud chcete získat aplikaci do tohoto stavu musíme nejprve odstranit celou řadu chyb.  
  
    ![Aplikace FlipView zobrazující očekávané výsledky](../debugger/media/js-dom-appfixed.png "JS_DOM_AppFixed")  
  
7. Zvolte buď **simulátor** nebo **palec Emulator 8.1 WVGA 4, 512MB** z rozevíracího seznamu vedle položky **spustit ladění** tlačítko **ladění**nástrojů:  
  
    ![Seznam cílů ladění vyberte](../debugger/media/js-select-target.png "JS_Select_Target")  
  
8. Zvolte **ladění** > **spustit ladění**, nebo stisknutím klávesy F5 spusťte aplikaci v režimu ladění.  
  
    To spustí aplikaci v emulátoru telefonu nebo simulátoru, ale uvidíte většinou prázdnou obrazovku, protože stylu v sobě obsahuje několik chyb. První `FlipView` v Čtvereček poblíž středu obrazovky se zobrazí obrázek.  
  
9. Pokud máte spuštěnou aplikaci v simulátoru, zvolte **rozlišení** příkazu panelu nástrojů na pravé straně simulátoru konfigurace rozlišení obrazovky 1 280 × 800. Tím se zajistí, že hodnoty uvedené v následujících krocích shodovat s v simulátoru.  
  
10. Přepněte do aplikace Visual Studio a zvolte **Průzkumníka modelu DOM** kartu.  
  
    > [!TIP]
    >  Můžete stisknutím Alt + Tab nebo F12 přepínat mezi Visual Studio a spuštěné aplikaci.  
  
11. V okně Průzkumníka modelu DOM, vyberte požadovaný prvek DIV oddílu, který má ID `"fView"`. Chcete-li zobrazit a vybrat správný prvek DIV pomocí kláves se šipkami. (Klávesy se šipkou doprava umožňuje zobrazit podřízené položky elementu.)  
  
     ![Průzkumník modelu DOM](../debugger/media/js-dom-explorer.png "JS_DOM_Explorer")  
  
    > [!TIP]
    >  Můžete také vybrat DIV element v levém dolním rohu okna konzoly jazyka JavaScript tak, že zadáte `select(fView)` na >> vstupní řádek a pak stiskněte klávesu Enter.  
  
     Hodnoty, které se zobrazují na karty na pravé straně okna Průzkumníka modelu DOM automaticky aktualizovat tak, aby odrážely v Průzkumníku modelu DOM aktuálního elementu.  
  
12. Zvolte **vypočítané** karty na pravé straně.  
  
     Tato karta zobrazuje vypočtená nebo konečné, hodnotu pro každou vlastnost vybraného prvku modelu DOM.  
  
13. Otevřete pravidlo výška šablony stylů CSS. Všimněte si, že je styl sady vložené do 100px, které se zobrazí konzistentní s hodnotou výška 100 %, nastavte pro `#fView` selektor šablon stylů CSS. Jako přeškrtnutý text pro `#fView` selektor označuje přiřazený styl je přednost před tímto stylem.  
  
     Je vidět na následujícím obrázku **vypočítané** kartu.  
  
     ![Vypočítat Průzkumníka modelu DOM kartu](../debugger/media/js-dom-explorer-computed.png "JS_DOM_Explorer_Computed")  
  
14. V hlavním okně Průzkumníka modelu DOM, dvakrát klikněte na panel přiřazený styl pro výšku a šířku `fView` DIV element. Teď můžete upravit hodnoty tady. V tomto scénáři chcete úplně odeberte.  
  
15. Vyberte `width: 100px;height: 100px;`, stiskněte klávesu Delete a potom stiskněte klávesu Enter. Po stisknutí klávesy Enter, nové hodnoty se okamžitě projeví v emulátoru telefonu nebo simulátoru, i když ještě zastavit ladicí relaci.  
  
    > [!IMPORTANT]
    >  Jak můžete aktualizovat atributy v okně Průzkumníka modelu DOM, můžete také aktualizovat hodnoty, které se zobrazují na **styly**, **vypočítané**, a **rozložení** karty. Další informace najdete v tématu [styly ladění šablon stylů CSS pomocí Průzkumníka modelu DOM](../debugger/debug-css-styles-using-dom-explorer.md) a [ladění rozložení pomocí Průzkumníka modelu DOM](../debugger/debug-layout-using-dom-explorer.md).  
  
16. Přepněte do aplikace tak, že vyberete Phone emulátoru nebo simulátoru, nebo pomocí kombinace kláves Alt + Tab.  
  
     Nyní `FlipView` ovládací prvek se zobrazí větší než velikost obrazovky telefonu emulátoru nebo simulátoru. Nejedná se odpovídající výsledek. K prozkoumání, přepněte zpět do sady Visual Studio.  
  
17. V Průzkumníku modelu DOM, vyberte **vypočítané** kartu znovu a otevřete pravidlo výšky. Prvek fView stále zobrazuje hodnota 100 %, podle očekávání z šablon stylů CSS, ale vypočítaná hodnota je rovna simulátoru výšku (pro příklad, 800px nebo 667.67px), který není vidíme pro tuto aplikaci. K prozkoumání, můžete odebrat výšku a šířku `fView` DIV element.  
  
18. V **styly** kartu, zrušte zaškrtnutí políčka vlastnosti výšku a šířku `#fView` selektor šablon stylů CSS.  
  
     **Vypočítané** karta nyní zobrazuje výšku 400 px. Informace o označuje, že tato hodnota pochází z modulu pro výběr .win flipview podle uživatelského rozhraní – dark.css, což je soubor CSS platformy.  
  
19. Přepněte zpět do aplikace.  
  
     Vylepšili věci. Existuje však ještě jeden další problém vyřešit: okraje zobrazí příliš velký.  
  
20. K prozkoumání, přepněte do aplikace Visual Studio a zvolte **rozložení** kartu a podívejte se na model pole elementu.  
  
     V **rozložení** kartě, zobrazí se vám následující hodnoty:  
  
    - Pro simulátor: 320px (posun) a 320px (okraj).  
  
    - Pro emulátor telefonu: 100px (posun) a 100px (okraj).  
  
      Následující ilustrace ukazuje jak **rozložení** karta bude vypadat, pokud používáte emulátor telefonu (100px posun a okraj).  
  
      ![Karta rozložení Průzkumníka modelu DOM](../debugger/media/js-dom-explorer-layout.png "JS_DOM_Explorer_Layout")  
  
      To vypadá, že nepodporuje správné. **Vypočítané** karta také zobrazuje stejné hodnoty vlastnosti okraj.  
  
21. Zvolte **styly** kartu a vyhledejte `#fView` selektor šablon stylů CSS. Zde se zobrazí hodnotu 25 % **okraj** vlastnost.  
  
22. Vyberte 25 % a změňte ho na 25px a stiskněte klávesu Enter.  
  
23. Také v **styly** kartu, vyberte pravidlo výšku pro selektor .win flipview a změňte 400 px na 500 px a stiskněte klávesu Enter.  
  
24. Přepněte zpět do aplikace a uvidíte, že umístění prvků se zobrazí správný. Opravit zdroj a aktualizovat aplikace bez zastavení a restartování ladicího programu, viz následující postup.  
  
#### <a name="to-refresh-your-app-while-debugging"></a>Chcete-li aktualizovat vaše aplikace během ladění  
  
1.  Zatímco aplikace stále běží, přepněte do sady Visual Studio.  
  
2.  Otevřete soubor default.html a upravit zdrojový kód tak, že změníte výšku a šířku `"fView"` elementu DIV na 100 %.  
  
3.  Zvolte **aktualizovat Windows app** tlačítko na panelu nástrojů ladění (nebo stisknutím klávesy F4). Tlačítko vypadá takto: ![tlačítko Aktualizovat Windows app](../debugger/media/js-refresh.png "JS_Refresh").  
  
     Znovu načíst stránky aplikace a simulátor nebo emulátor telefonu vrátí do popředí.  
  
     Další informace o funkci aktualizace najdete v tématu [aktualizace aplikace (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
##  <a name="SelectingElements"></a> Výběr elementů  
 Při ladění aplikace, můžete vybrat prvky modelu DOM třemi způsoby:  
  
- Po kliknutí na prvky přímo v okně Průzkumníka modelu DOM (nebo pomocí kláves se šipkami).  
  
- S použitím **vybrat Element** tlačítko (Ctrl + B).  
  
- S použitím `select` příkaz, který je jedním z [příkazy konzoly jazyka JavaScript](../debugger/javascript-console-commands.md).  
  
  Použijete-li vybrat elementy a umístěte ukazatel myši na prvek okna Průzkumníka modelu DOM, odpovídající prvek je zvýrazněn ve spuštěné aplikaci. Musíte kliknout na elementu v Průzkumníku modelu DOM se vybere nebo můžete použít klávesy se šipkami ke zvýraznění a vybrat elementy. Můžete také vybrat elementy v Průzkumníku modelu DOM pomocí **Select element** tlačítko. Je vidět na následujícím obrázku **vybrat Element** tlačítko.  
  
  ![Vybrat Element v Průzkumníku modelu DOM](../debugger/media/js-dom-select-element-button.png "JS_DOM_Select_Element_Button")  
  
  Po kliknutí na **Select element** (nebo stiskněte klávesy Ctrl + B), to změní režim výběru, takže můžete vybrat položku v Průzkumníku modelu DOM kliknutím ve spuštěné aplikaci. Režim změny zpět do režimu výběru normální po kliknutí. Po kliknutí na **Select element**, aplikace bude zase na popředí a kurzor se změní na odrážejí nový režim výběru. Po kliknutí na prvek obrysy Průzkumníka modelu DOM se vrátí do popředí s Zadaný prvek vybraný.  
  
  Než se rozhodnete **vybrat Element**, můžete určit, zda zvýrazněte elementů v běžící aplikaci přepnutím **zobrazení webové stránky zvýrazní** tlačítko. Následující obrázek znázorňuje toto tlačítko. Stručný přehled se zobrazí ve výchozím nastavení.  
  
  ![Zobrazení webové stránky zvýrazní tlačítko](../debugger/media/js-dom-display-highlights-button.png "JS_DOM_Display_Highlights_Button")  
  
  Pokud budete chtít zvýraznit elementy, jsou zvýrazněny prvky, které najedete myší v simulátoru. Barvy pro zvýrazněné elementy odpovídat pole modelu, který se zobrazí **rozložení** karty Průzkumníku modelu DOM.  
  
> [!NOTE]
>  Zvýrazňování elementů podržením ukazatele nad nich je jenom částečně podporovány v emulátoru Windows Phone.  
  
 Příklad, který ukazuje, jak vybrat prvky pomocí **Select element** tlačítko, naleznete v tématu [styly ladění šablon stylů CSS pomocí Průzkumníka modelu DOM](../debugger/debug-css-styles-using-dom-explorer.md).  
  
##  <a name="BrowserSupport"></a> Prohlížeče a Platformní podpory  
 Nástroje sady Visual Studio pro jazyk JavaScript, Průzkumníka modelu DOM a okna konzoly jazyka JavaScript jsou podporované na následujících platformách:  
  
- [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] a aplikací pro Windows Phone Store v jazyce JavaScript a HTML  
  
- Internet Explorer 11 a systémem [!INCLUDE[win81](../includes/win81-md.md)]  
  
- Aplikace Internet Explorer 10 a systémem [!INCLUDE[win8](../includes/win8-md.md)]  
  
  Přejděte [tady](http://go.microsoft.com/fwlink/?LinkID=232448) Stáhnout [!INCLUDE[win8](../includes/win8-md.md)] a sady Visual Studio.  
  
## <a name="see-also"></a>Viz také  
 [Ladění aplikací v sadě Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   
 [Ladění stylů CSS pomocí Průzkumníka modelu DOM](../debugger/debug-css-styles-using-dom-explorer.md)   
 [Ladění rozložení pomocí Průzkumníka modelu DOM](../debugger/debug-layout-using-dom-explorer.md)   
 [Zobrazení naslouchacích procesů událostí DOM](../debugger/view-dom-event-listeners.md)   
 [Aktualizace aplikace (JavaScript)](../debugger/refresh-an-app-javascript.md)   
 [Ladění ovládacího prvku WebView](../debugger/debug-a-webview-control.md)   
 [Klávesové zkratky](../debugger/keyboard-shortcuts-html-and-javascript.md)   
 [Příkazy konzoly jazyka JavaScript](../debugger/javascript-console-commands.md)   
 [Ladění ukázkový kód HTML, CSS a JavaScript](../debugger/debug-html-css-and-javascript-sample-code.md)   
 [Technická podpora a usnadnění přístupu](http://msdn.microsoft.com/library/tzbxw1af\(VS.120\).aspx)



