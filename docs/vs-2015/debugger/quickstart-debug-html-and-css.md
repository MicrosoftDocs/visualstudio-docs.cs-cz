---
title: 'Rychlý Start: ladění HTML a CSS | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: be85bd5c09d59df576d66cef6cf2d4e7e34876ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687654"
---
# <a name="quickstart-debug-html-and-css"></a>Rychlý start: Ladění kódu HTML a CSS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Pro aplikace JavaScriptu nabízí Visual Studio komplexní ladicí prostředí, které zahrnuje funkce, které jsou známé pro vývojáře v aplikacích Internet Explorer a Visual Studio. Tyto funkce jsou podporované pro aplikace [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] Windows Phone Store a pro aplikace vytvořené pomocí Visual Studio Tools pro Apache Cordova  
  
 Pomocí modelu interaktivního ladění, který poskytuje nástroje pro kontrolu DOM, můžete zobrazit a upravit vykreslený kód HTML a CSS. To všechno můžete udělat bez zastavení a restartování ladicího programu.  
  
 V tomto tématu:  
  
- [Kontrola živého modelu DOM](#InspectingDOM)  
  
- [Výběr elementů](#SelectingElements)  
  
  Další informace o používání Průzkumníka modelu DOM naleznete v následujících tématech:  
  
- [Ladění stylů CSS pomocí průzkumníka modelu DOM](../debugger/debug-css-styles-using-dom-explorer.md)  
  
- [Ladění rozložení pomocí průzkumníka modelu DOM](../debugger/debug-layout-using-dom-explorer.md)  
  
- [Zobrazení naslouchacích procesů událostí DOM](../debugger/view-dom-event-listeners.md)  
  
- [Aktualizace aplikace (JavaScript)](../debugger/refresh-an-app-javascript.md)  
  
- [Ladění ovládacího prvku WebView](../debugger/debug-a-webview-control.md)  
  
  Informace o dalších funkcích ladění JavaScriptu, jako je použití okna konzoly JavaScriptu a nastavení zarážek, najdete v tématu [rychlý Start: ladění JavaScriptu](../debugger/quickstart-debug-javascript-using-the-console.md) a [ladění aplikací v aplikaci Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
## <a name="inspecting-the-live-dom"></a><a name="InspectingDOM"></a> Kontrola živého modelu DOM  
 Průzkumník modelu DOM zobrazuje vykreslenou stránku a k změně hodnot a okamžitému zobrazení výsledků můžete použít Průzkumníka modelu DOM. To umožňuje testovat změny bez zastavení a restartování ladicího programu. Zdrojový kód v projektu se při interakci se stránkou nemění pomocí této metody, takže pokud najdete požadované opravy kódu, provedete změny ve zdrojovém kódu.  
  
> [!TIP]
> Abyste se vyhnuli zastavení a restartování ladicího programu při provádění změn ve zdrojovém kódu, můžete aplikaci aktualizovat pomocí tlačítka **aktualizovat aplikaci pro Windows** na panelu nástrojů ladění (nebo stisknutím klávesy F4). Další informace najdete v tématu [aktualizace aplikace (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
 Průzkumník modelu DOM můžete použít k těmto akcím:  
  
- Procházejte podstrom elementu modelu DOM a prozkoumejte vykreslený kód HTML, CSS a JavaScript.  
  
- Dynamické úpravy atributů a stylů CSS pro vykreslené elementy a okamžité zobrazení výsledků.  
  
- Zkontrolujte, jak byly použity styly CSS na prvky stránky a trasovat pravidla, která byla použita.  
  
  Při ladění aplikací je často nutné vybrat prvky v Průzkumníku modelu DOM. Když vyberete prvek, hodnoty, které se zobrazí na kartách na pravé straně Průzkumníka modelu DOM, se automaticky aktualizují tak, aby odrážely vybraný prvek v Průzkumníku modelu DOM. Toto jsou karty: **Styles**, **vypočítaná**, **layout**. Aplikace pro Windows Store také podporují karty **události** a **změny** . Další informace o výběru prvků naleznete v tématu [Select Elements](#SelectingElements).  
  
> [!TIP]
> Pokud je okno Průzkumníka modelu DOM zavřeno, klikněte na položku **ladit** > **Windows**  >  **DOM Explorer** a znovu ji otevřete. Okno se zobrazí pouze během relace ladění skriptu.  
  
 V následujícím postupu projdeme proces interaktivního ladění aplikace pomocí Průzkumníka modelu DOM. Vytvoříme aplikaci, která používá `FlipView` ovládací prvek a pak ho bude ladit. Aplikace obsahuje několik chyb.  
  
> [!WARNING]
> Tato ukázková aplikace je aplikace pro Windows Store. Pro Cordova se podporují stejné funkce, ale aplikace se liší.  
  
#### <a name="to-debug-by-inspecting-the-live-dom"></a>Ladění pomocí živého modelu DOM  
  
1. Vytvořte nové řešení v aplikaci Visual Studio tak, že kliknete na **soubor**  >  **Nový projekt**.  
  
2. Zvolte možnost **JavaScript**  >  **úložiště**JavaScriptu, zvolte **aplikace pro Windows** nebo **aplikace Windows Phone**a pak zvolte **prázdná aplikace**.  
  
3. Zadejte název projektu, například `FlipViewApp` , a kliknutím na **tlačítko OK** vytvořte aplikaci.  
  
4. Do prvku tělo default.html přidejte tento kód:  
  
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
  
5. Otevřete default. CSS a přidejte následující šablony stylů CSS:  
  
   ```css  
   #fView {  
       background-color:#0094ff;  
       height: 100%;  
       width: 100%;  
       margin: 25%;  
   }  
   ```  
  
6. Nahraďte kód v default.js tímto kódem:  
  
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
  
    Následující ilustrace ukazuje, co chceme zjistit, pokud tuto aplikaci spustíme v emulátoru telefonu (vypadá podobně jako v simulátoru). Pokud ale chcete aplikaci získat do tohoto stavu, musíme nejdřív opravit několik chyb.  
  
    ![Aplikace FlipView zobrazující očekávané výsledky](../debugger/media/js-dom-appfixed.png "JS_DOM_AppFixed")  
  
7. Z rozevíracího seznamu vedle tlačítka **Spustit ladění** na panelu nástrojů **ladění** vyberte **simulátor** nebo **emulátor 8,1 WVGA 4 palce** .  
  
    ![Vybrat cílový seznam pro ladění](../debugger/media/js-select-target.png "JS_Select_Target")  
  
8. Zvolte **ladění**  >  **Spustit ladění**nebo stiskněte klávesu F5 a spusťte aplikaci v režimu ladění.  
  
    Tím se aplikace spustí v simulátoru nebo v emulátoru telefonu, ale zobrazí se většinou prázdná obrazovka, protože tento styl obsahuje několik chyb. První `FlipView` Obrázek se zobrazí v malém čtverečku uprostřed obrazovky.  
  
9. Pokud spouštíte aplikaci v simulátoru, klikněte na příkaz panelu nástrojů **změnit rozlišení** na pravé straně simulátoru a nakonfigurujte rozlišení obrazovky 1280 x 800. Tím se zajistí, že hodnoty uvedené v následujících krocích odpovídají tomu, co vidíte v simulátoru.  
  
10. Přepněte do sady Visual Studio a vyberte kartu **Průzkumník modelu DOM** .  
  
    > [!TIP]
    > Můžete stisknout ALT + TAB nebo F12 a přepínat mezi sadou Visual Studio a běžící aplikací.  
  
11. V okně Průzkumník modelu DOM vyberte element DIV pro oddíl, který má ID `"fView"` . Pomocí šipkových kláves můžete zobrazit a vybrat správný prvek DIV. (Klávesa šipka doprava umožňuje zobrazit podřízené prvky elementu.)  
  
     ![Průzkumník modelu DOM](../debugger/media/js-dom-explorer.png "JS_DOM_Explorer")  
  
    > [!TIP]
    > Můžete také vybrat element DIV v levém dolním rohu okna konzoly JavaScriptu zadáním `select(fView)` >> vstupní výzvy a stisknutím klávesy ENTER.  
  
     Hodnoty, které se zobrazí na kartách na pravé straně okna Průzkumníka modelu DOM, se automaticky aktualizují tak, aby odrážely aktuální prvek v Průzkumníku modelu DOM.  
  
12. Na pravé straně vyberte kartu **vypočítané** .  
  
     Tato karta zobrazuje vypočtenou nebo konečnou hodnotu pro každou vlastnost vybraného prvku modelu DOM.  
  
13. Otevřete pravidlo výška šablony stylů CSS. Všimněte si, že je vložená sada stylů nastavená na 100px, která se jeví jako nekonzistentní s hodnotou výšky 100% nastavenou pro `#fView` Selektor šablon stylů CSS. Přeškrtnutí textu pro `#fView` selektor značí, že vložený styl má přednost před tímto stylem.  
  
     Následující ilustrace znázorňuje **vypočítanou** kartu.  
  
     ![Vypočítaná karta Průzkumníka modelu DOM](../debugger/media/js-dom-explorer-computed.png "JS_DOM_Explorer_Computed")  
  
14. V hlavním okně Průzkumníka modelu DOM dvakrát klikněte na vložený styl pro výšku a šířku `fView` elementu div. Nyní můžete upravit hodnoty. V tomto scénáři je chceme zcela odebrat.  
  
15. Vyberte `width: 100px;height: 100px;` , stiskněte klávesu DELETE a potom stiskněte klávesu ENTER. Po stisknutí klávesy ENTER se nové hodnoty okamžitě projeví v simulátoru nebo v emulátoru telefonu, i když jste nezastavili relaci ladění.  
  
    > [!IMPORTANT]
    > Jak můžete aktualizovat atributy v okně Průzkumníka modelu DOM, můžete také aktualizovat hodnoty, které se zobrazí na kartách **styly**, **vypočítané**a **rozložení** . Další informace naleznete v tématu [Ladění stylů CSS pomocí Průzkumníka modelu DOM](../debugger/debug-css-styles-using-dom-explorer.md) a [rozložení ladění pomocí Průzkumníka modelu DOM](../debugger/debug-layout-using-dom-explorer.md).  
  
16. Přepněte do aplikace výběrem simulátoru nebo emulátoru telefonu nebo pomocí ALT + TAB.  
  
     Nyní `FlipView` se ovládací prvek zobrazuje větší než velikost obrazovky simulátoru nebo emulátoru telefonu. Nejedná se o zamýšlený výsledek. Chcete-li prověřit, přepněte zpět do sady Visual Studio.  
  
17. V Průzkumníku modelu DOM vyberte znovu **vypočítanou** kartu a otevřete pravidlo výšky. Element fView stále zobrazuje hodnotu 100%, jak je očekáváno v šabloně stylů CSS, ale vypočtená hodnota se rovná výšce obrazovky simulátoru (například 800px nebo 667.67 px), která není pro tuto aplikaci žádoucí. K prozkoumání můžete odebrat výšku a šířku pro `fView` element div.  
  
18. Na kartě **styly** zrušte výběr vlastnosti výška a šířka v `#fView` selektoru šablon stylů CSS.  
  
     **Vypočítaná** karta teď zobrazuje výšku 400px. Informace značí, že tato hodnota pochází z selektoru. Win-FlipView, který je zadaný v souboru UI-Dark. CSS, což je soubor CSS platformy.  
  
19. Přepněte zpátky do aplikace.  
  
     Vylepšili jsme věci. Stále však existuje ještě ještě jeden problém, který by bylo možné opravit: okraje jsou příliš velké.  
  
20. Chcete-li prověřit, přepněte do sady Visual Studio a klikněte na kartu **rozložení** a podívejte se na model pole prvku.  
  
     Na kartě **rozložení** se zobrazí následující hodnoty:  
  
    - Pro simulátor: 320px (offset) a 320px (okraj).  
  
    - Pro emulátor telefonu: 100px (posun) a 100px (okraj).  
  
      Následující ilustrace znázorňuje, jak vypadá karta **rozložení** , pokud používáte emulátor telefonu (posun 100px a okraj).  
  
      ![Karta rozložení Průzkumníka modelu DOM](../debugger/media/js-dom-explorer-layout.png "JS_DOM_Explorer_Layout")  
  
      To se nezdá být správné. **Vypočítaná** karta obsahuje také stejné hodnoty okrajů.  
  
21. Klikněte na kartu **styly** a vyhledejte `#fView` Selektor šablon stylů CSS. Tady se u vlastnosti **marže** zobrazí hodnota 25%.  
  
22. Vyberte 25% a změňte jej na 25px a stiskněte klávesu ENTER.  
  
23. Také na kartě **styly** zvolte pravidlo výšky pro selektor. Win-FlipView a změňte 400px na 500 px a stiskněte klávesu ENTER.  
  
24. Přepněte zpátky do aplikace a uvidíte, že umístění prvků je správné. Chcete-li opravit zdroj a aktualizovat aplikaci bez zastavení a restartování ladicího programu, přečtěte si následující postup.  
  
#### <a name="to-refresh-your-app-while-debugging"></a>Aktualizace aplikace při ladění  
  
1. I když je aplikace stále spuštěná, přepněte do sady Visual Studio.  
  
2. Otevřete default.html a upravte svůj zdrojový kód tak, že změníte výšku a šířku `"fView"` elementu div na 100%.  
  
3. Klikněte na tlačítko **aktualizovat aplikaci pro Windows** na panelu nástrojů ladění (nebo stiskněte F4). Tlačítko vypadá takto: ![tlačítko Aktualizovat aplikaci pro Windows](../debugger/media/js-refresh.png "JS_Refresh").  
  
     Stránky aplikace se znovu načítají a simulátor nebo telefonní emulátor se vrátí do popředí.  
  
     Další informace o funkci aktualizovat najdete v tématu [aktualizace aplikace (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
## <a name="selecting-elements"></a><a name="SelectingElements"></a> Výběr elementů  
 Při ladění aplikace můžete vybrat prvky DOM třemi způsoby:  
  
- Kliknutím na prvky přímo v okně Průzkumníka modelu DOM (nebo pomocí kláves se šipkami).  
  
- Pomocí tlačítka **vybrat element** (CTRL + B).  
  
- Pomocí `select` příkazu, který je jedním z [příkazů konzole jazyka JavaScript](../debugger/javascript-console-commands.md).  
  
  Použijete-li okno Průzkumníka modelu DOM k výběru prvků a umístíte ukazatel myši na prvek, je ve spuštěné aplikaci zvýrazněn odpovídající prvek. Je nutné kliknout na prvek v Průzkumníku modelu DOM a vybrat jej, nebo můžete použít klávesy se šipkami pro zvýraznění a výběr prvků. Můžete také vybrat prvky v Průzkumníku modelu DOM pomocí tlačítka **vybrat element** . Na následujícím obrázku je znázorněno tlačítko **vybrat element** .  
  
  ![Tlačítko vybrat element v Průzkumníkovi modelu DOM](../debugger/media/js-dom-select-element-button.png "JS_DOM_Select_Element_Button")  
  
  Když kliknete na **vybrat element** (nebo stisknete CTRL + B), změní se režim výběru tak, aby bylo možné vybrat položku v Průzkumníkovi modelu DOM kliknutím na ni v běžící aplikaci. Režim se po jednom kliknutí změní zpátky na režim normálního výběru. Když kliknete na **vybrat element**, aplikace přichází do popředí a kurzor se změní tak, aby odrážel nový režim výběru. Po kliknutí na prvek s přířádkou, se Průzkumník DOM vrátí na popředí se zadaným elementem.  
  
  Předtím, než zvolíte **možnost vybrat element**, můžete určit, zda chcete zvýraznit prvky ve spuštěné aplikaci přepnutím tlačítka **Zobrazit webovou stránku světla** . Toto tlačítko je znázorněno na následujícím obrázku. Ve výchozím nastavení se zobrazují světla.  
  
  ![Zobrazit tlačítko zvýraznění webové stránky](../debugger/media/js-dom-display-highlights-button.png "JS_DOM_Display_Highlights_Button")  
  
  Pokud se rozhodnete zvýraznit prvky, prvky, na které ukazatel myši v simulátoru zvýrazníte, se zvýrazní. Barvy pro zvýrazněné elementy se shodují s modelem pole, který se zobrazí na kartě **rozložení** Průzkumníka modelu DOM.  
  
> [!NOTE]
> Zvýraznění prvků přesunutím myší na ně je pouze částečně podporováno v emulátoru Windows Phone.  
  
 Příklad, který ukazuje, jak vybrat prvky pomocí tlačítka **vybrat element** , naleznete v tématu [Ladění stylů CSS pomocí Průzkumníka modelu DOM](../debugger/debug-css-styles-using-dom-explorer.md).  
  
## <a name="browser-and-platform-support"></a><a name="BrowserSupport"></a> Podpora prohlížečů a platforem  
 Nástroje Visual Studio Tools for JavaScript, Průzkumník modelu DOM a okno konzoly JavaScriptu jsou podporovány na následujících platformách:  
  
- [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] a aplikace Windows Phone Storu pomocí JavaScriptu a HTML  
  
- Internet Explorer 11 běžící na [!INCLUDE[win81](../includes/win81-md.md)]  
  
- Internet Explorer 10 běžící na [!INCLUDE[win8](../includes/win8-md.md)]  
  
  [Zde](https://developer.microsoft.com/windows/downloads/sdk-archive) si můžete stáhnout [!INCLUDE[win8](../includes/win8-md.md)] a sady Visual Studio.  
  
## <a name="see-also"></a>Viz také  
 [Ladění aplikací v aplikaci Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   
 [Ladění stylů CSS pomocí Průzkumníka modelu DOM](../debugger/debug-css-styles-using-dom-explorer.md)   
 [Ladit rozložení pomocí Průzkumníka modelu DOM](../debugger/debug-layout-using-dom-explorer.md)   
 [Zobrazit naslouchací procesy událostí modelu DOM](../debugger/view-dom-event-listeners.md)   
 [Aktualizace aplikace (JavaScript)](../debugger/refresh-an-app-javascript.md)   
 [Ladění ovládacího prvku WebView](../debugger/debug-a-webview-control.md)   
 [Klávesové zkratky](../debugger/keyboard-shortcuts-html-and-javascript.md)   
 [Příkazy konzoly JavaScriptu](../debugger/javascript-console-commands.md)   
 [Ladění ukázkového kódu HTML, CSS a JavaScript](../debugger/debug-html-css-and-javascript-sample-code.md)   
 [Podpora produktu a usnadnění](https://msdn.microsoft.com/library/tzbxw1af\(VS.120\).aspx)
