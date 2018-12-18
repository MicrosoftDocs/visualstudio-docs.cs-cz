---
title: Ladění stylů CSS pomocí Průzkumníka modelu DOM | Dokumentace Microsoftu
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
- CSS styles [Windows Store apps], debugging
- CSS rules [Windows Store apps], debugging
- CSS debugging [Windows Store apps]
- debugging, CSS rules [Windows Store apps]
- HTML debugging [Windows Store apps]
ms.assetid: 2dfef7c6-7db2-4550-b694-783b0e535cea
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f5a2c8ef6792403628430cb9881b24e6e279f02
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750153"
---
# <a name="debug-css-styles-using-dom-explorer"></a>Ladění stylů CSS pomocí průzkumníka modelu DOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Při ladění aplikace Windows Store, Windows Phone Store, aplikací a aplikací vytvořených pomocí Visual Studio Tools pro Apache Cordova, můžete zobrazit a změnit pravidla šablon stylů CSS pro vybrané elementy modelu DOM a jejich podřízené prvky.  
  
 **Styly** a **vypočítané** karty v Průzkumníku modelu DOM zobrazují pravidla šablon stylů CSS, které platí pro vybraný element. Pravidla jsou zobrazena v pořadí jejich specifičnosti podle časové posloupnosti pravidel šablon stylů CSS. Pravidla, která se na kartě v selektoru nebo u stylu zobrazují nahoře (nejspecifičtější pravidla), se na zvolený element aplikují jako poslední a pravidla, která se zobrazují dole, se aplikují jako první. Jakmile jsou pravidla aplikována, přepíšou dříve použitá pravidla.  
  
 **Styly**, **vypočítané**, a **změny** karty poskytují různá zobrazení informací o stylu.  
  
-   Použití **styly** kartu k zobrazení pravidel uspořádaných podle názvu selektoru šablon stylů CSS, jako například `html, body`. Tuto kartu lze také použít pro povolení nebo zakázání určitých stylů, manuální nastavení hodnot nebo okamžité zobrazení výsledků těchto změn.  
  
-   Použití **vypočítané** kartu pro zobrazení vypočtených hodnot stylu. Pokud například nastavíte velikost na 1em, hodnota vypočítaná aplikací Internet Explorer může být 16px. Styly na této kartě jsou uspořádány podle názvu stylu, například `height`. Tuto kartu lze také použít pro povolení nebo zakázání určitých stylů, manuální nastavení hodnot nebo okamžité zobrazení výsledků těchto změn.  
  
    > [!NOTE]
    >  Ve Visual Studio 2013 Update 2, informace uvedené **trasování** kartu byl sloučen s **vypočítané** kartu a **trasování** byla odebrána.  
  
-   Použití **změny** kartě (pouze aplikace Windows Store a Windows Phone Store) k identifikaci a sledování stylů CSS, které byly změněny během relace ladění.  
  
> [!TIP]
>  Změny provedené na styly **styly** a **vypočítané** karty nejsou trvalé. Jsou ztraceny, jakmile zastavíte ladění. Pokud chcete změnit zdrojový kód a znovu načíst stránky bez zastavení a restartování ladicího programu, aktualizujte aplikaci pomocí ![tlačítko Aktualizovat Windows app](../debugger/media/js-refresh.png "JS_Refresh") tlačítko (**aplikace aktualizovat Windows** ) na **ladění** nástrojů (pouze aplikace Windows Store a Windows Phone Store). Další informace najdete v tématu [aktualizace aplikace (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
## <a name="example-of-fixing-a-css-rule"></a>Příklad opravy pravidla šablony stylů CSS  
 Tento příklad ukazuje, jak zkontrolovat pravidla šablony stylů CSS a jak ladit problémy se stylem. Například Řekněme, že chcete změnit barvu písma použitého pro zobrazení názvů skupin v [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] šabloně rozdělené aplikace.  
  
> [!NOTE]
>  Tento příklad ukazuje aplikace Windows Store, ale také použít všechny zobrazené funkce Průzkumníku modelu DOM do aplikace pro Windows Phone Store a, s výjimkou kartě změny aplikace vytvořená pomocí nástrojů Visual Studio pro Apache Cordova.  
  
#### <a name="to-view-and-change-css-rules"></a>Zobrazení nebo změna pravidel šablon stylů CSS  
  
1.  V sadě Visual Studio, vytvořit [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace pomocí jazyků JavaScript a HTML v šabloně projektu rozdělené aplikace.  
  
2.  V **Průzkumníka řešení**, otevřete items.css. (Items.css najdete ve složce stránky.)  
  
3.  Nahraďte následující kód šablony stylů CSS:  
  
    ```css  
    .itemspage .itemslist .item {  
        -ms-grid-columns: 1fr;  
        -ms-grid-rows: 1fr 90px;  
        display: -ms-grid;  
        height: 250px;  
        width: 250px;  
    }  
    ```  
  
     tímto kódem:  
  
    ```css  
    .itemspage .itemslist .item {  
        -ms-grid-columns: 1fr;  
        -ms-grid-rows: 1fr 90px;  
        display: -ms-grid;  
        height: 250px;  
        width: 250px;  
        color: #ff6a00;  
    }  
    ```  
  
     Přidáte tak styl, který určuje barvu #ff6a00 (oranžová) pro každou položku v seznamu. Selektor šablon stylů CSS `.itemspage .itemslist .item`, označuje sadu názvů tříd pro prvky elementů DIV v items.html, které se zobrazí jako vnořené elementy v živém `item` DIV element specifikuje položky seznamu.  
  
4.  Vyberte **simulátor** v rozevíracím seznamu na **ladění** nástrojů (**místního počítače** je výchozí hodnota).  
  
     ![Seznam cílů ladění vyberte](../debugger/media/js-select-target.png "JS_Select_Target")  
  
5.  Stisknutím klávesy F5 spusťte aplikaci v režimu ladění.  
  
     Po dokončení načítání aplikace, vyhledejte záhlaví položek seznamu, jako například **název skupiny: 1**. Barva se nezměnila, takže pokus o použití oranžové barvy v názvech selhal. S pomocí karet šablon stylů CSS v průzkumníku modelu DOM zjistíme, co bylo špatně, a chybu napravíme.  
  
    > [!TIP]
    >  Jakmile se aplikace objeví v simulátoru, umístěte simulátor vpravo vedle okna aplikace Visual Studio, okamžitě tak uvidíte výsledky výběru a provedené změny stylů CSS.  
  
6.  Přepněte do aplikace Visual Studio a klikněte na tlačítko **vybrat Element** v Průzkumníku modelu DOM (nebo stiskněte kombinaci kláves Ctrl + B). Změní se režim výběru, takže budete moci kliknutím vybrat položku a aplikace se zobrazí v popředí. Po kliknutí se režim přepne zpět. Tady je **vybrat Element** tlačítko. ![Vybrat Element v Průzkumníku modelu DOM](../debugger/media/js-dom-select-element-button.png "JS_DOM_Select_Element_Button")  
  
    > [!TIP]
    >  Můžete také vybrat elementy HTML přímo v průzkumníku modelu DOM. Další informace o výběru elementů naleznete v tématu [rychlý start: ladění kódu HTML a CSS](../debugger/quickstart-debug-html-and-css.md).  
  
7.  V simulátoru, umístěte kurzor na název první položky v seznamu **název skupiny: 1**, v levém panelu domovské stránky. Název je zvýrazněn, jak je znázorněno zde:  
  
     ![Pomocí tlačítka Vybrat Element](../debugger/media/js-css-select-element.png "JS_CSS_Select_Element")  
  
    > [!NOTE]
    >  Emulátor Windows Phone jen částečně podporuje zvýrazňování elementů podržením ukazatele.  
  
8.  Klikněte na vyznačený název. Průzkumník modelu DOM automaticky vybere odpovídající element HTML, který vypadá podobně jako tento.  
  
    ```html  
    <h4 class="item-title">Group Title: 1</h4>  
    ```  
  
     Vyberete-li v průzkumníku modelu DOM element H4, karty průzkumníku modelu DOM zobrazí pravidla přidružená k elementu H4. **Vypočítané** kartě se zobrazí zde s `color` otevřenou vlastností:  
  
     ![Karta styly trasování v Průzkumníku modelu DOM](../debugger/media/js-css-styles.png "JS_CSS_Styles")  
  
     Toto zobrazení obsahuje užitečné informace o pravidlech, která jsou přidružené k `color` styl, jako je následující:  
  
    -   Selektor šablon stylů CSS, který je upraven v items.css, `.itemspage .itemslist .item`, se nepoužívá v konečném výpočtu stylu (zobrazí se jako přeškrtnutý text). Několik dalších výskytů `color` stylu nepoužívá se ani.  
  
        > [!TIP]
        >  U delších názvů selektoru se plný název zobrazí v popisu tlačítka.  
  
    -   Konečná vypočítaná hodnota šablon stylů CSS, `rgba(255, 255, 255, 0.87)`, je nastavena speciálně pro následující selektor šablon stylů CSS: `.itemspage .itemslist .item .item-overlay .item-title`, který je definován také v items.css.  
  
        > [!TIP]
        >  Teď, když víme, kde nastavit barvu názvu, víme také, kde ji můžeme změnit. Změny v průzkumníku modelu DOM však můžeme otestovat také bez obnovení aplikace, jak je popsáno ve zbývajících krocích.  
  
9. Zrušte zaškrtnutí políčka pro první výskyt `color` styl, který je `.itemspage .itemslist .item .item-overlay .item-title` selektor. Nyní v simulátoru vidíte, že názvy barev položky změnila na oranžovou, jak jsme chtěli, a selektor, který jsme modifikovali v jazyce CSS, `.itemspage .itemslist .item`, již není přepsán (to znamená, že už nemá přeškrtnutý text). Tady je **vypočítané** kartě Po zaškrtnutí políčka.  
  
     ![Na kartě vypočítané po aktualizaci stylu CSS](../debugger/media/js-css-styles-fixed.png "JS_CSS_Styles_Fixed")  
  
10. Vyberte **změny** kartu.  
  
     Použití **změny** kartu pro identifikaci a sledování změn stylů, které jste provedli během relace ladění. Je vidět na následujícím obrázku `.itemspage .itemslist .item .item-overlay .item-title` oblasti pro výběr **změny** kartu, která je teď přepsána.  
  
     ![Karta změny Průzkumníka modelu DOM](../debugger/media/js-css-styles-changes.png "JS_CSS_Styles_Changes")  
  
11. Můžete také ručně upravit hodnoty stylů CSS a výsledky lze okamžitě zobrazit pomocí **styly** kartu.  
  
12. Vyberte **styly** kartu.  
  
13. Otevřít `.itemspage .itemslist .item .item-overlay .item-title` selektor stylů.  
  
14. Vyberte první výskyt `color` stylu a potom dvakrát klikněte na hodnotu vlastnosti `rgb(255, 255, 255, 0.87)`.  
  
15. Tuto hodnotu můžete změnit pomocí klávesnice. Změňte ho na `rgb(255, 255, 0, 0.87)`, a potom stiskněte klávesu Enter. Barvy všech názvů položek v simulátoru se změní na žlutou.  
  
16. Chcete-li provést změny ve zdrojovém souboru šablon stylů CSS, klikněte na tlačítko **items.css** odkaz na **styly** kartu. Otevře se items.css, kde můžete změnit hodnotu `color` styl v kódu vaší aplikace. Chcete-li aktualizovat aplikace bez zastavení a restartování ladicího programu, klikněte na tlačítko ![tlačítko Aktualizovat Windows app](../debugger/media/js-refresh.png "JS_Refresh") (**aktualizovat Windows app**) tlačítko na **Ladění** nástrojů.  
  
## <a name="see-also"></a>Viz také  
 [Rychlý start: Ladění kódu HTML a CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Ladění rozložení pomocí Průzkumníka modelu DOM](../debugger/debug-layout-using-dom-explorer.md)   
 [Zobrazení naslouchacích procesů událostí DOM](../debugger/view-dom-event-listeners.md)   
 [Technická podpora a usnadnění přístupu](http://go.microsoft.com/fwlink/?LinkId=253502)



