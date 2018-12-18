---
title: Ladění rozložení pomocí Průzkumníka modelu DOM | Dokumentace Microsoftu
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
- box model [Windows Store apps], viewing
- debugging layout [Windows Store apps]
- layout, debugging [Windows Store apps]
ms.assetid: ded6566d-fc29-49a7-8029-dee8e50fe733
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba06e6a8ba95887c0cc6b6acfd14cef10ff03798
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787743"
---
# <a name="debug-layout-using-dom-explorer"></a>Ladění rozložení pomocí průzkumníka modelu DOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 **Rozložení** karty Průzkumníku modelu DOM zobrazí [šablon stylů CSS rámečkový model](http://go.microsoft.com/fwlink/?LinkID=238778) pro vybraný element ve [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace, aplikace Windows Phone Store nebo aplikace vytvořená pomocí nástrojů Visual Studio pro Apache Cordova. Tento vizuální reprezentaci modelu pole můžete použít k identifikaci a změnit rozložení související hodnoty, které mají vliv vzhled elementů.  
  
> [!TIP]
>  Změny provedené v **rozložení** kartě nejsou trvalé. Můžete dělat trvalé změny zdrojového kódu a pak aktualizujte aplikaci pomocí **aktualizovat Windows app** tlačítko (pouze aplikace Windows Store a Windows Phone Store) na panelu nástrojů ladění. Díky tomu se můžete vyhnout restartování ladicího programu.  
  
 Úprava stránky rozložení, které nejsou zobrazeny v modelu pole pomocí Průzkumníka modelu DOM, naleznete v tématu [rychlý start: ladění kódu HTML a CSS](../debugger/quickstart-debug-html-and-css.md) a [styly ladění šablon stylů CSS pomocí Průzkumníka modelu DOM](../debugger/debug-css-styles-using-dom-explorer.md).  
  
## <a name="example-of-fixing-a-layout-issue"></a>Příklad opravy problému rozložení  
 Tento příklad ukazuje, jak vybrat seznam element v šabloně Centrum/Pivot, interpretovat pole hodnoty modelu, které jsou na **rozložení** kartu a potom změňte jednu z hodnot vlastností rozložení problém vyřešit.  
  
#### <a name="to-fix-the-layout-issue"></a>Chcete-li vyřešit tento problém rozložení  
  
1.  V sadě Visual Studio vytvořte novou aplikaci Store, který používá šablonu projektu centra/Pivot.  
  
2.  Ve složce sdílené pages\hub otevřete hub.css.  
  
3.  Nahraďte následující kód šablony stylů CSS:  
  
    ```css  
    .hubpage .hub .section4 .sub-image-row img {  
        height: 95px;  
        width: 130px;  
    }  
    ```  
  
     s tímto kódem šablon stylů CSS:  
  
    ```css  
    .hubpage .hub .section4 .sub-image-row img {  
        height: 95px;  
        width: 130px;  
        margin-left: 5em;  
    }  
    ```  
  
4.  V Průzkumníku řešení vyberte projekt appName.WindowsPhone nebo appName.Windows projektu a klikněte na tlačítko **nastavit jako spouštěný projekt** z místní nabídky pro projekt.  
  
5.  V závislosti na spouštěný projekt, zvolte buď **palec Emulator 8.1 WVGA 4, 512 MB** nebo **simulátor** v rozevíracím seznamu na panelu nástrojů ladění (**místního počítače** je výchozí nastavení hodnota).  
  
     ![Výběr cíle ladění](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")  
  
6.  Stisknutím klávesy F5 spusťte aplikaci v režimu ladění.  
  
7.  Otevřete část 4 posouvání nebo flicking.  
  
    > [!TIP]
    >  Pozice Phone emulátor ani simulátor vpravo vedle okna sady Visual Studio, protože okamžitě uvidíte výsledky výběru a změny stylů CSS.  
  
     Když se načte 4 části, naleznete v tématu nižší imagí nevypadají správně. Vyjmutí na polovinu (s levé poloviční chybějící) se zobrazí každý obrázek položky.  
  
8.  Přepněte do aplikace Visual Studio a zvolte **vybrat Element** v Průzkumníku modelu DOM (nebo stiskněte kombinaci kláves Ctrl + B). Změní se režim výběru, takže budete moci kliknutím vybrat položku a aplikace se zobrazí v popředí. Po kliknutí se režim přepne zpět.  
  
    > [!TIP]
    >  Vybrat elementy HTML přímo v Průzkumníku modelu DOM můžete také použít klávesy se šipkami nebo jiné metody. Další informace o výběru elementů naleznete v tématu [rychlý start: ladění kódu HTML a CSS](../debugger/quickstart-debug-html-and-css.md).  
  
9. V emulátoru telefonu nebo simulátoru vyberte šedou pravé polovině některou k imagí, které se odstraní v polovině. Zvýraznění se objeví kolem vybraný prvek, jak je vidět v emulátoru Windows Phone:  
  
     ![Výběr prvku modelu DOM](../debugger/media/js-css-layout-select.png "JS_CSS_Layout_Select")  
  
    > [!TIP]
    >  Simulátor podporuje prvky zobrazit pole zvýraznění kolem elementů modelu DOM dřív, než vyberete jeden ukazatel myši. Emulátor Windows Phone to nepodporuje.  
  
     Když vyberete prvek modelu DOM, Průzkumníka modelu DOM automaticky vybere odpovídající element IMG v sadě Visual Studio. Element vybrána v Průzkumníku modelu DOM vypadá takto:  
  
    ```html  
    <img src="ms-appx://guid/images/gray.png>   
    </img>  
    ```  
  
10. Klikněte na tlačítko **rozložení** kartu. Tato karta zobrazuje pole modelu vybraného prvku, jak je vidět v emulátoru Windows Phone.  
  
     ![Rozložení karty Průzkumníku modelu DOM](../debugger/media/js-css-layout.png "JS_CSS_Layout")  
  
     Toto zobrazení obsahuje některé užitečné informace o elementu:  
  
    -   Barvy odpovídají pole zvýraznění, který se zobrazí v simulátoru, když ukazatel myši přesunout prvky. Představuje modrou barvu \<img > elementu dimenze. Tan barva představuje hodnoty vlastnosti okraj.  
  
    -   Je nastavena na levý okraj (levého okraje), který pomocné parametry na příčinu problému protože odpovídá příznaku (černá na levé straně imagí).  
  
    -   Pole, která zobrazí hodnoty 0 pixelů (například okraje a odsazení) naznačují, že odpovídající vlastnosti šablon stylů CSS, pravděpodobně není nastavené.  
  
11. Pokud chcete zjistit, jak je okraj doleva pravidlo použito, zvolte **vypočítané** kartu a podívejte se do části pravidlo okraj doleva. Uvidíte, že toto pravidlo se nastaví pomocí 5em hodnotu, ale je vypočítaná hodnota 66.66px nebo 146.66px, v závislosti na cílové zařízení.  
  
    > [!TIP]
    >  **Vypočítané** kartě se zobrazí, že je levý okraj pravidlo nastavené `..hubpage .hub. section4 .sub-image-row img` selektor šablon stylů CSS v hub.css nalezen. V této ukázkové aplikaci, která je, kde budete muset provést opravu.  
  
     Můžete také použít **rozložení** kartu k testování změny hodnot rozložení.  
  
12. V **rozložení** záložce **66.66** nebo **146.66**, který se objevuje v **okraj** pole na levé straně pole.  
  
13. Typ `0` a stiskněte klávesu Enter. (Můžete také použít kláves Šipka nahoru a Šipka dolů ke změně hodnoty).  
  
14. Vyberte druhou \<img > prvků v Průzkumníku modelu DOM a změnit jejich okraj doleva hodnoty na hodnotu 0.  
  
15. Přepnout na emulátoru telefonu nebo na simulátoru. Oddíl 4 Image se použily aktualizovanými hodnotami okraj doleva. Tyto hodnoty jsou aktualizované taky v **vypočítané** kartu podle pravidla okraj doleva.  
  
## <a name="see-also"></a>Viz také  
 [Rychlý start: Ladění kódu HTML a CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Ladění stylů CSS pomocí Průzkumníka modelu DOM](../debugger/debug-css-styles-using-dom-explorer.md)   
 [Zobrazení naslouchacích procesů událostí DOM](../debugger/view-dom-event-listeners.md)



