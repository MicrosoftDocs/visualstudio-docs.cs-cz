---
title: Ladění HTML a CSS v aplikacích pro UWP | Microsoft Docs
ms.date: 07/17/2018
ms.topic: how-to
f1_keywords:
- VS.WebClient.DomExplorer
dev_langs:
- JavaScript
helpviewer_keywords:
- debugging, CSS
- debugging, HTML
- debugging, JavaScript [UWP apps]
- DOM Explorer [UWP apps]
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: a43ac0930c4805d18c60a18e1b48882b2fed76de
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600181"
---
# <a name="debug-html-and-css-in-uwp-apps-in-visual-studio"></a>Ladění HTML a CSS v aplikacích pro UWP v aplikaci Visual Studio

Pro aplikace JavaScriptu nabízí Visual Studio komplexní ladicí prostředí, které zahrnuje funkce, které jsou známé pro vývojáře v aplikacích Internet Explorer a Visual Studio. Tyto funkce jsou podporované pro aplikace pro UWP a pro aplikace vytvořené pomocí Visual Studio Tools Apache Cordova.

Pomocí modelu interaktivního ladění, který poskytuje nástroje pro kontrolu DOM, můžete zobrazit a upravit vykreslený kód HTML a CSS. To všechno můžete udělat bez zastavení a restartování ladicího programu.

Informace o dalších funkcích ladění JavaScriptu, jako je použití okna konzoly JavaScriptu a nastavení zarážek, najdete v tématu [rychlý Start: ladění JavaScriptu](../debugger/quickstart-debug-javascript-using-the-console.md) a [ladění aplikací v aplikaci Visual Studio](debugging-windows-store-and-windows-universal-apps.md).

## <a name="inspecting-the-live-dom"></a><a name="InspectingDOM"></a> Kontrola živého modelu DOM
Průzkumník modelu DOM zobrazuje vykreslenou stránku a k změně hodnot a okamžitému zobrazení výsledků můžete použít Průzkumníka modelu DOM. To umožňuje testovat změny bez zastavení a restartování ladicího programu. Zdrojový kód v projektu se při interakci se stránkou nemění pomocí této metody, takže pokud najdete požadované opravy kódu, provedete změny ve zdrojovém kódu.

> [!TIP]
> Abyste se vyhnuli zastavení a restartování ladicího programu při provádění změn ve zdrojovém kódu, můžete aplikaci aktualizovat pomocí tlačítka **aktualizovat aplikaci pro Windows** na panelu nástrojů ladění (nebo stisknutím klávesy F4). Další informace najdete v tématu [aktualizace aplikace (JavaScript)](../debugger/refresh-an-app-javascript.md).

Průzkumník modelu DOM můžete použít k těmto akcím:

- Procházejte podstrom elementu modelu DOM a prozkoumejte vykreslený kód HTML, CSS a JavaScript.

- Dynamické úpravy atributů a stylů CSS pro vykreslené elementy a okamžité zobrazení výsledků.

- Zkontrolujte, jak byly použity styly CSS na prvky stránky a trasovat pravidla, která byla použita.

  Při ladění aplikací je často nutné vybrat prvky v Průzkumníku modelu DOM. Když vyberete prvek, hodnoty, které se zobrazí na kartách na pravé straně Průzkumníka modelu DOM, se automaticky aktualizují tak, aby odrážely vybraný prvek v Průzkumníku modelu DOM. Toto jsou karty: **Styles**, **vypočítaná**, **layout**. Aplikace pro UWP také podporují karty **události** a **změny** . Další informace o výběru prvků naleznete v tématu [Select Elements](#SelectingElements).

> [!TIP]
> Pokud je okno Průzkumníka modelu DOM zavřeno, klikněte na položku **ladit** > **Windows**  >  **DOM Explorer** a znovu ji otevřete. Okno se zobrazí pouze během relace ladění skriptu.

V následujícím postupu projdeme proces interaktivního ladění aplikace pomocí Průzkumníka modelu DOM. Vytvoříme aplikaci, která používá `FlipView` ovládací prvek a pak ho bude ladit. Aplikace obsahuje několik chyb.

> [!WARNING]
> Tato ukázková aplikace je aplikace pro UWP. Pro Cordova se podporují stejné funkce, ale aplikace se liší.

#### <a name="to-debug-by-inspecting-the-live-dom"></a>Ladění pomocí živého modelu DOM

1. Vytvořte nové řešení v aplikaci Visual Studio tak, že kliknete na **soubor**  >  **Nový projekt**.

2. Zvolte **JavaScript**  >  **Windows Universal**a pak zvolte **aplikace WinJS**.

3. Zadejte název projektu, například `FlipViewApp` , a kliknutím na **tlačítko OK** vytvořte aplikaci.

4. Do prvku tělo index.html přidejte tento kód:

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

            pages.setAt(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
            pages.setAt(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });
            pages.setAt(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });
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

    Následující ilustrace ukazuje, co chceme zjistit, pokud tuto aplikaci spouštíme. Pokud ale chcete aplikaci získat do tohoto stavu, musíme nejdřív opravit několik chyb.

    ![Aplikace FlipView zobrazující očekávané výsledky](../debugger/media/js_dom_appfixed.png "JS_DOM_AppFixed")

7. V rozevíracím seznamu vedle tlačítka **Spustit ladění** na panelu nástrojů **ladění** vyberte **místní počítač** :

    ![Vybrat cílový seznam pro ladění](../debugger/media/js_select_target.png "JS_Select_Target")

8. Zvolte **ladění**  >  **Spustit ladění**nebo stiskněte klávesu F5 a spusťte aplikaci v režimu ladění.

    Tím se aplikace spustí, ale zobrazí se většinou prázdná obrazovka, protože tento styl obsahuje několik chyb. První `FlipView` Obrázek se zobrazí v malém čtverečku uprostřed obrazovky.

9. Přepněte do sady Visual Studio a vyberte kartu **Průzkumník modelu DOM** .

    > [!TIP]
    > Můžete stisknout ALT + TAB nebo F12 a přepínat mezi sadou Visual Studio a běžící aplikací.

10. V okně Průzkumník modelu DOM vyberte element DIV pro oddíl, který má ID `"fView"` . Pomocí šipkových kláves můžete zobrazit a vybrat správný prvek DIV. (Klávesa šipka doprava umožňuje zobrazit podřízené prvky elementu.)

    ![Průzkumník modelu DOM](../debugger/media/js_dom_explorer.png "JS_DOM_Explorer")

    > [!TIP]
    > Můžete také vybrat element DIV v levém dolním rohu okna konzoly JavaScriptu zadáním `select(fView)` >> vstupní výzvy a stisknutím klávesy ENTER.

    Hodnoty, které se zobrazí na kartách na pravé straně okna Průzkumníka modelu DOM, se automaticky aktualizují tak, aby odrážely aktuální prvek v Průzkumníku modelu DOM.

11. Na pravé straně vyberte kartu **vypočítané** .

    Tato karta zobrazuje vypočtenou nebo konečnou hodnotu pro každou vlastnost vybraného prvku modelu DOM.

12. Otevřete pravidlo výška šablony stylů CSS. Všimněte si, že je vložená sada stylů nastavená na 100px, která se jeví jako nekonzistentní s hodnotou výšky 100% nastavenou pro `#fView` Selektor šablon stylů CSS. Přeškrtnutí textu pro `#fView` selektor značí, že vložený styl má přednost před tímto stylem.

    Následující ilustrace znázorňuje **vypočítanou** kartu.

    ![Vypočítaná karta Průzkumníka modelu DOM](../debugger/media/js_dom_explorer_computed.png "JS_DOM_Explorer_Computed")

13. V hlavním okně Průzkumníka modelu DOM dvakrát klikněte na vložený styl pro výšku a šířku `fView` elementu div. Nyní můžete upravit hodnoty. V tomto scénáři je chceme zcela odebrat.

14. V hlavním okně klikněte dvakrát na tlačítko `width: 100px;height: 100px;` , stiskněte klávesu **Delete** a potom stiskněte klávesu **ENTER**. Po stisknutí klávesy ENTER se nové hodnoty v aplikaci okamžitě projeví, i když jste nezastavili relaci ladění.

    > [!IMPORTANT]
    > Jak můžete aktualizovat atributy v okně Průzkumníka modelu DOM, můžete také aktualizovat hodnoty, které se zobrazí na kartách **styly**, **vypočítané**a **rozložení** .

15. Přepněte na aplikaci tak, že ji vyberete nebo použijete ALT + TAB.

    Nyní `FlipView` se ovládací prvek zobrazuje větší než velikost obrazovky simulátoru nebo emulátoru telefonu. Nejedná se o zamýšlený výsledek. Chcete-li prověřit, přepněte zpět do sady Visual Studio.

16. V Průzkumníku modelu DOM vyberte znovu **vypočítanou** kartu a otevřete pravidlo výšky. Element fView stále zobrazuje hodnotu 100%, jak je očekáváno v šabloně stylů CSS, ale vypočtená hodnota se rovná výšce obrazovky aplikace (například 800px, 667.67 px nebo jiné hodnotě), která není pro tuto aplikaci žádoucí. Chcete-li prozkoumat, v dalších krocích odeberu výšku a šířku pro `fView` element div.

17. Na kartě **styly** zrušte výběr vlastnosti výška a šířka v `#fView` selektoru šablon stylů CSS.

    **Vypočítaná** karta teď zobrazuje výšku 400px. Informace značí, že tato hodnota pochází z selektoru. Win-FlipView, který je zadaný v souboru UI-Dark. CSS, což je soubor CSS platformy.

18. Přepněte zpátky do aplikace.

    Vylepšili jsme věci. Stále však existuje ještě ještě jeden problém, který by bylo možné opravit: okraje jsou příliš velké.

19. Chcete-li prověřit, přepněte do sady Visual Studio a klikněte na kartu **rozložení** a podívejte se na model pole prvku.

    Na kartě **rozložení** se zobrazí následující:

    - 255px (posunutí) a 255px (okraj) nebo podobné hodnoty v závislosti na rozlišení zařízení.

      Následující ilustrace znázorňuje, jak karta **rozložení** vypadá, pokud používáte emulátor s 100px posunem a okrajem.

      ![Karta rozložení Průzkumníka modelu DOM](../debugger/media/js_dom_explorer_layout.png "JS_DOM_Explorer_Layout")

      To se nezdá být správné. **Vypočítaná** karta obsahuje také stejné hodnoty okrajů.

20. Klikněte na kartu **styly** a vyhledejte `#fView` Selektor šablon stylů CSS. Tady se u vlastnosti **marže** zobrazí hodnota 25%.

21. Vyberte 25% a změňte jej na 25px a stiskněte klávesu ENTER.

22. Také na kartě **styly** zvolte pravidlo výšky pro selektor. Win-FlipView a změňte 400px na 500 px a stiskněte klávesu ENTER.

23. Přepněte zpátky do aplikace a uvidíte, že umístění prvků je správné. Chcete-li opravit zdroj a aktualizovat aplikaci bez zastavení a restartování ladicího programu, přečtěte si následující postup.

#### <a name="to-refresh-your-app-while-debugging"></a>Aktualizace aplikace při ladění

1. I když je aplikace stále spuštěná, přepněte do sady Visual Studio.

2. Otevřete default.html a upravte svůj zdrojový kód tak, že změníte výšku a šířku `"fView"` elementu div na 100%.

3. Klikněte na tlačítko **aktualizovat aplikaci pro Windows** na panelu nástrojů ladění (nebo stiskněte F4). Tlačítko vypadá takto: ![tlačítko Aktualizovat aplikaci pro Windows](../debugger/media/js_refresh.png "JS_Refresh").

    Stránky aplikace se znovu načítají a simulátor nebo telefonní emulátor se vrátí do popředí.

    Další informace o funkci aktualizovat najdete v tématu [aktualizace aplikace (JavaScript)](../debugger/refresh-an-app-javascript.md).

## <a name="selecting-elements"></a><a name="SelectingElements"></a> Výběr elementů
Při ladění aplikace můžete vybrat prvky DOM třemi způsoby:

- Kliknutím na prvky přímo v okně Průzkumníka modelu DOM (nebo pomocí kláves se šipkami).

- Pomocí tlačítka **vybrat element** (CTRL + B).

- Pomocí `select` příkazu, který je jedním z [příkazů konzole jazyka JavaScript](../debugger/javascript-console-commands.md?view=vs-2017).

  Použijete-li okno Průzkumníka modelu DOM k výběru prvků a umístíte ukazatel myši na prvek, je ve spuštěné aplikaci zvýrazněn odpovídající prvek. Je nutné kliknout na prvek v Průzkumníku modelu DOM a vybrat jej, nebo můžete použít klávesy se šipkami pro zvýraznění a výběr prvků. Můžete také vybrat prvky v Průzkumníku modelu DOM pomocí tlačítka **vybrat element** . Na následujícím obrázku je znázorněno tlačítko **vybrat element** .

  ![Tlačítko vybrat element v Průzkumníkovi modelu DOM](../debugger/media/js_dom_select_element_button.png "JS_DOM_Select_Element_Button")

  Když kliknete na **vybrat element** (nebo stisknete CTRL + B), změní se režim výběru tak, aby bylo možné vybrat položku v Průzkumníkovi modelu DOM kliknutím na ni v běžící aplikaci. Režim se po jednom kliknutí změní zpátky na režim normálního výběru. Když kliknete na **vybrat element**, aplikace přichází do popředí a kurzor se změní tak, aby odrážel nový režim výběru. Po kliknutí na prvek s přířádkou, se Průzkumník DOM vrátí na popředí se zadaným elementem.

  Předtím, než zvolíte **možnost vybrat element**, můžete určit, zda chcete zvýraznit prvky ve spuštěné aplikaci přepnutím tlačítka **Zobrazit webovou stránku světla** . Toto tlačítko je znázorněno na následujícím obrázku. Ve výchozím nastavení se zobrazují světla.

  ![Zobrazit tlačítko zvýraznění webové stránky](../debugger/media/js_dom_display_highlights_button.png "JS_DOM_Display_Highlights_Button")

  Pokud se rozhodnete zvýraznit prvky, prvky, na které ukazatel myši v simulátoru zvýrazníte, se zvýrazní. Barvy pro zvýrazněné elementy se shodují s modelem pole, který se zobrazí na kartě **rozložení** Průzkumníka modelu DOM.

> [!NOTE]
> Zvýraznění prvků přesunutím myší na ně je pouze částečně podporováno v emulátoru Windows Phone.

## <a name="see-also"></a>Viz také

- [Ladění aplikací v sadě Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
- [Aktualizace aplikace (JavaScript)](../debugger/refresh-an-app-javascript.md)
- [Ladění ovládacího prvku WebView](../debugger/debug-a-webview-control.md)
- [Klávesové zkratky](../debugger/keyboard-shortcuts-html-and-javascript.md?view=vs-2017)
- [Příkazy konzoly jazyka JavaScript](../debugger/javascript-console-commands.md?view=vs-2017)
- [Ladění vzorového kódu HTML, CSS a JavaScript](../debugger/debug-html-css-and-javascript-sample-code.md)
- [Podpora produktu a usnadnění](/previous-versions/tzbxw1af(v=vs.120))