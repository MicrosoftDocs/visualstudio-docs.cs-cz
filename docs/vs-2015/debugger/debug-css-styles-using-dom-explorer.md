---
title: Ladění stylů CSS pomocí Průzkumníka modelu DOM | Microsoft Docs
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
- CSS styles [Windows Store apps], debugging
- CSS rules [Windows Store apps], debugging
- CSS debugging [Windows Store apps]
- debugging, CSS rules [Windows Store apps]
- HTML debugging [Windows Store apps]
ms.assetid: 2dfef7c6-7db2-4550-b694-783b0e535cea
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a9f07fc064a87910f59f5734d4d635aa3b5d6b77
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299503"
---
# <a name="debug-css-styles-using-dom-explorer"></a>Ladění stylů CSS pomocí průzkumníka modelu DOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Když ladíte aplikace pro Windows Store, aplikace Windows Phone Storu a aplikace vytvořené pomocí Visual Studio Tools pro Apache Cordova, můžete zobrazit a změnit pravidla šablony stylů CSS pro vybrané prvky modelu DOM a jejich podřízené prvky.  
  
 Karty **styly** a **vypočítané** v Průzkumníkovi modelu DOM zobrazují pravidla šablony stylů CSS, která se vztahují na vybraný prvek. Pravidla jsou zobrazena v pořadí jejich specifičnosti podle časové posloupnosti pravidel šablon stylů CSS. Pravidla, která se na kartě v selektoru nebo u stylu zobrazují nahoře (nejspecifičtější pravidla), se na zvolený element aplikují jako poslední a pravidla, která se zobrazují dole, se aplikují jako první. Jakmile jsou pravidla aplikována, přepíšou dříve použitá pravidla.  
  
 Karty **styly**, **vypočítané**a **změny** poskytují různá zobrazení informací o stylu.  
  
- Použijte kartu **styly** k zobrazení pravidel uspořádaných podle názvu selektoru šablon stylů CSS, například `html, body`. Tuto kartu lze také použít pro povolení nebo zakázání určitých stylů, manuální nastavení hodnot nebo okamžité zobrazení výsledků těchto změn.  
  
- Použijte **vypočítanou** kartu k zobrazení vypočítaných hodnot stylu. Pokud například nastavíte velikost na 1em, hodnota vypočítaná aplikací Internet Explorer může být 16px. Styly na této kartě jsou uspořádány podle názvu stylu, například `height`. Tuto kartu lze také použít pro povolení nebo zakázání určitých stylů, manuální nastavení hodnot nebo okamžité zobrazení výsledků těchto změn.  
  
    > [!NOTE]
    > V Visual Studio 2013 Update 2 se informace uvedené na kartě **trasování** sloučily pomocí karty **vypočítané** a karta **trasování** se odebrala.  
  
- Použijte kartu **změny** (pouze aplikace pro Windows store a Windows Phone Store) k identifikaci a sledování stylů CSS, které jste změnili během relace ladění.  
  
> [!TIP]
> Změny, které provedete v stylech na **stylech** a **vypočítaných** záložkách, nejsou trvalé. Jsou ztraceny, jakmile zastavíte ladění. Chcete-li změnit zdrojový kód a znovu načíst stránky bez zastavení a restartování ladicího programu, aktualizujte aplikaci pomocí tlačítka pro obnovení aplikace systému ![Windows](../debugger/media/js-refresh.png "JS_Refresh") (**aktualizovat aplikaci systému Windows**) na panelu nástrojů **ladění** (pouze aplikace pro Windows Store a Windows Phone Store). Další informace najdete v tématu [aktualizace aplikace (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
## <a name="example-of-fixing-a-css-rule"></a>Příklad opravy pravidla šablony stylů CSS  
 Tento příklad ukazuje, jak zkontrolovat pravidla šablony stylů CSS a jak ladit problémy se stylem. V tomto příkladu řekněme, že chcete změnit barvu písma používaného k zobrazení názvů skupin v šabloně [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] rozdělit aplikaci.  
  
> [!NOTE]
> Tento příklad ukazuje aplikaci pro Windows Store, ale všechny zobrazené funkce Průzkumníka modelu DOM platí také pro aplikaci Windows Phone Store a s výjimkou karty změny, aplikace vytvořená pomocí Visual Studio Tools pro Apache Cordova.  
  
#### <a name="to-view-and-change-css-rules"></a>Zobrazení nebo změna pravidel šablon stylů CSS  
  
1. V aplikaci Visual Studio vytvořte aplikaci [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] pomocí JavaScriptu a HTML v šabloně projektu rozdělené aplikace.  
  
2. V **Průzkumník řešení**otevřete položku Items. CSS. (Items.css najdete ve složce stránky.)  
  
3. Nahraďte následující kód šablony stylů CSS:  
  
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
  
     Přidáte tak styl, který určuje barvu #ff6a00 (oranžová) pro každou položku v seznamu. Selektor šablon stylů CSS, `.itemspage .itemslist .item`, označuje sadu názvů tříd pro elementy DIV v Items. html, které se zobrazí jako vnořené prvky v živém modelu DOM. Prvek `item` DIV určuje položky seznamu.  
  
4. V rozevíracím seznamu na panelu nástrojů **ladění** vyberte **simulátor** (výchozí hodnota je**místní počítač** ).  
  
     ![Vybrat cílový seznam pro ladění](../debugger/media/js-select-target.png "JS_Select_Target")  
  
5. Stisknutím klávesy F5 spusťte aplikaci v režimu ladění.  
  
     Po dokončení načítání aplikace se podívejte na záhlaví položek seznamu, jako je například **název skupiny: 1**. Barva se nezměnila, takže pokus o použití oranžové barvy v názvech selhal. S pomocí karet šablon stylů CSS v průzkumníku modelu DOM zjistíme, co bylo špatně, a chybu napravíme.  
  
    > [!TIP]
    > Jakmile se aplikace objeví v simulátoru, umístěte simulátor vpravo vedle okna aplikace Visual Studio, okamžitě tak uvidíte výsledky výběru a provedené změny stylů CSS.  
  
6. Přepněte do sady Visual Studio a klikněte na **vybrat element** v Průzkumníku modelu DOM (nebo stiskněte CTRL + B). Změní se režim výběru, takže budete moci kliknutím vybrat položku a aplikace se zobrazí v popředí. Po kliknutí se režim přepne zpět. Tady je tlačítko **vybrat element** . ![Tlačítko vybrat element v Průzkumníkovi modelu DOM](../debugger/media/js-dom-select-element-button.png "JS_DOM_Select_Element_Button ")  
  
    > [!TIP]
    > Můžete také vybrat elementy HTML přímo v průzkumníku modelu DOM. Další informace o výběru prvků naleznete v tématu [rychlý Start: ladění HTML a CSS](../debugger/quickstart-debug-html-and-css.md).  
  
7. V simulátoru umístěte ukazatel myši na název první položky v seznamu, **název skupiny: 1**, a to v levém panelu domovské stránky. Název je zvýrazněn, jak je znázorněno zde:  
  
     ![Použití tlačítka vybrat element](../debugger/media/js-css-select-element.png "JS_CSS_Select_Element")  
  
    > [!NOTE]
    > Emulátor Windows Phone pouze částečně podporuje zvýrazňování prvků najetím myší.  
  
8. Klikněte na vyznačený název. Průzkumník modelu DOM automaticky vybere odpovídající element HTML, který vypadá podobně jako tento.  
  
    ```html  
    <h4 class="item-title">Group Title: 1</h4>  
    ```  
  
     Vyberete-li v průzkumníku modelu DOM element H4, karty průzkumníku modelu DOM zobrazí pravidla přidružená k elementu H4. Tady se zobrazí **vypočítaná** karta s otevřenou vlastností `color`:  
  
     ![Karta styly trasování v Průzkumníkovi modelu DOM](../debugger/media/js-css-styles.png "JS_CSS_Styles")  
  
     Toto zobrazení poskytuje užitečné informace o pravidlech, která jsou přidružená k `color` stylu, například k následujícím akcím:  
  
    - Selektor šablon stylů CSS, který jsme změnili v Items. CSS, `.itemspage .itemslist .item`, se nepoužívá v konečném výpočtu stylu (zobrazuje se v přeškrtnutí textu). Nepoužívá se ani několik dalších výskytů stylu `color`.  
  
        > [!TIP]
        > U delších názvů selektoru se plný název zobrazí v popisu tlačítka.  
  
    - Konečná vypočtená hodnota CSS, `rgba(255, 255, 255, 0.87)`, je nastavena speciálně pro následující Selektor šablon stylů CSS: `.itemspage .itemslist .item .item-overlay .item-title`, který je také definován v Items. CSS.  
  
        > [!TIP]
        > Teď, když víme, kde nastavit barvu názvu, víme také, kde ji můžeme změnit. Změny v průzkumníku modelu DOM však můžeme otestovat také bez obnovení aplikace, jak je popsáno ve zbývajících krocích.  
  
9. Zrušte zaškrtnutí políčka u prvního výskytu stylu `color`, který je pro selektor `.itemspage .itemslist .item .item-overlay .item-title`. Nyní se v simulátoru zobrazí, že barva názvů položek se všechny změnila na oranžovou, jak jsme zamýšleli, a selektor, který jsme změnili v CSS, `.itemspage .itemslist .item`, již není přepsán (to znamená, že již nepoužívá přeškrtnutí textu). Tady je **vypočítaná** karta po zrušení zaškrtnutí políčka.  
  
     ![Vypočítaná karta po aktualizaci stylu CSS](../debugger/media/js-css-styles-fixed.png "JS_CSS_Styles_Fixed")  
  
10. Vyberte kartu **změny** .  
  
     Pomocí karty **změny** můžete identifikovat a sledovat změny stylu, které jste provedli během relace ladění. Následující ilustrace znázorňuje `.itemspage .itemslist .item .item-overlay .item-title` selektor na kartě **změny** , která je nyní přepsána.  
  
     ![Karta změny v Průzkumníkovi modelu DOM](../debugger/media/js-css-styles-changes.png "JS_CSS_Styles_Changes")  
  
11. Můžete také ručně upravovat hodnoty stylu CSS a zobrazit okamžitý výsledek pomocí karty **styly** .  
  
12. Vyberte kartu **styly** .  
  
13. Otevřete selektor stylu `.itemspage .itemslist .item .item-overlay .item-title`.  
  
14. Vyberte první výskyt stylu `color` a potom dvakrát klikněte na hodnotu vlastnosti `rgb(255, 255, 255, 0.87)`.  
  
15. Tuto hodnotu můžete změnit pomocí klávesnice. Změňte ji na `rgb(255, 255, 0, 0.87)`a potom stiskněte klávesu ENTER. Barvy všech názvů položek v simulátoru se změní na žlutou.  
  
16. Chcete-li provést změny zdrojového souboru šablon stylů CSS, klikněte na odkaz **Items. CSS** na kartě **styly** . Tím se otevře položka. CSS, kde můžete změnit hodnotu stylu `color` v kódu aplikace. Pokud chcete aplikaci aktualizovat bez zastavení a restartování ladicího programu, klikněte na tlačítko ![aktualizovat aplikaci pro Windows](../debugger/media/js-refresh.png "JS_Refresh") (**Obnovit aplikaci systému Windows**) na panelu nástrojů **ladění** .  
  
## <a name="see-also"></a>Viz také  
 [Rychlý Start: ladění HTML a CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Ladit rozložení pomocí Průzkumníka modelu DOM](../debugger/debug-layout-using-dom-explorer.md)   
 [Zobrazit naslouchací procesy událostí modelu DOM](../debugger/view-dom-event-listeners.md)   
 [Podpora produktu a usnadnění](https://go.microsoft.com/fwlink/?LinkId=253502)
