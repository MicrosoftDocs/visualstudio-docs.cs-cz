---
title: Ladění rozložení pomocí Průzkumníka modelu DOM | Microsoft Docs
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
- box model [Windows Store apps], viewing
- debugging layout [Windows Store apps]
- layout, debugging [Windows Store apps]
ms.assetid: ded6566d-fc29-49a7-8029-dee8e50fe733
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1a3c9b3a6ae2ed11e8512f8cf8857d27b3d0043b
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850075"
---
# <a name="debug-layout-using-dom-explorer"></a>Ladění rozložení pomocí průzkumníka modelu DOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Karta **rozložení** v Průzkumníkovi modelu DOM zobrazuje [model pole CSS](https://www.w3.org/TR/CSS2/box.html) pro vybraný prvek v aplikaci [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)], aplikaci Windows Phone Storu nebo aplikaci vytvořenou pomocí Visual Studio Tools pro Apache Cordova. Tato vizuální reprezentace modelu box slouží k identifikaci a úpravám hodnot souvisejících s rozložením, které mají vliv na vzhled prvků.  
  
> [!TIP]
> Změny, které provedete na kartě **rozložení** , nejsou trvalé. Můžete provádět trvalé změny ve zdrojovém kódu a pak aktualizovat aplikaci pomocí tlačítka **aktualizovat aplikaci pro Windows** (pouze aplikace pro Windows store a Windows Phone Store) na panelu nástrojů ladění. Tímto způsobem se můžete vyhnout restartování ladicího programu.  
  
 Chcete-li použít Průzkumníka modelu DOM k úpravě aspektů rozložení, které nejsou uvedeny v modelu pole, přečtěte si téma [rychlý Start: ladění HTML a CSS](../debugger/quickstart-debug-html-and-css.md) a [Ladění stylů CSS pomocí Průzkumníka modelu DOM](../debugger/debug-css-styles-using-dom-explorer.md).  
  
## <a name="example-of-fixing-a-layout-issue"></a>Příklad opravy problému s rozložením  
 Tento příklad ukazuje, jak vybrat prvek seznamu v šabloně hub/Pivot, interpretovat hodnoty modelu pole, které jsou na kartě **rozložení** , a pak změnit jednu z hodnot vlastností pro opravu problému s rozložením.  
  
#### <a name="to-fix-the-layout-issue"></a>Oprava problému s rozložením  
  
1. V aplikaci Visual Studio vytvořte novou aplikaci ze Storu, která používá šablonu projektu hub/Pivot.  
  
2. Ve složce Shared pages\hub otevřete hub. CSS.  
  
3. Nahraďte následující kód šablony stylů CSS:  
  
    ```css  
    .hubpage .hub .section4 .sub-image-row img {  
        height: 95px;  
        width: 130px;  
    }  
    ```  
  
     s tímto kódem CSS:  
  
    ```css  
    .hubpage .hub .section4 .sub-image-row img {  
        height: 95px;  
        width: 130px;  
        margin-left: 5em;  
    }  
    ```  
  
4. Vyberte projekt appName. WindowsPhone nebo název_aplikace. Windows v Průzkumník řešení a pak zvolte **nastavit jako projekt po spuštění** z místní nabídky projektu.  
  
5. V závislosti na spouštěném projektu vyberte buď možnost **emulátor 8,1 WVGA 4 palce 512 MB** nebo **simulátor** v rozevíracím seznamu na panelu nástrojů ladění (výchozí hodnota je**místní počítač** ).  
  
     ![Výběr cíle ladění](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")  
  
6. Stisknutím klávesy F5 spusťte aplikaci v režimu ladění.  
  
7. Otevřete oddíl 4 posouváním nebo pohybem prstem.  
  
    > [!TIP]
    > Polohu emulátoru telefonu nebo simulátoru hned vedle okna sady Visual Studio, takže můžete okamžitě zobrazit výsledky vašich výběrů a změny, které provedete u stylů CSS.  
  
     Při načtení oddílu 4 vidíte, že se spodní obrázky nehledají správně. Obrázek každého položky se zobrazí jako vyjmutý z poloviny (s levou polovinou chybí).  
  
8. Přepněte do sady Visual Studio a zvolte **vybrat element** v Průzkumníku modelu DOM (nebo stiskněte CTRL + B). Změní se režim výběru, takže budete moci kliknutím vybrat položku a aplikace se zobrazí v popředí. Po kliknutí se režim přepne zpět.  
  
    > [!TIP]
    > Můžete také použít klávesy se šipkami nebo jiné metody a vybrat prvky HTML přímo v Průzkumníku modelu DOM. Další informace o výběru prvků naleznete v tématu [rychlý Start: ladění HTML a CSS](../debugger/quickstart-debug-html-and-css.md).  
  
9. V emulátoru telefonu nebo simulátoru vyberte šedou pravou polovinu jednoho z obrázků, které jsou vyjmuty na polovinu. Zvýraznění se zobrazí kolem vybraného prvku, jak je znázorněno v emulátoru Windows Phone:  
  
     ![Výběr elementu modelu DOM](../debugger/media/js-css-layout-select.png "JS_CSS_Layout_Select")  
  
    > [!TIP]
    > Simulátor podporuje najetí myší nad prvky pro zobrazení zvýraznění rámečku kolem elementů modelu DOM před výběrem některého z nich. Emulátor Windows Phone tuto podporu nepodporuje.  
  
     Když vyberete prvek modelu DOM, Průzkumník modelu DOM automaticky vybere odpovídající element IMG v aplikaci Visual Studio. Element vybraný v Průzkumníku modelu DOM vypadá takto:  
  
    ```html  
    <img src="ms-appx://guid/images/gray.png>   
    </img>  
    ```  
  
10. Klikněte na kartu **rozložení** . Tato karta zobrazuje model pole vybraného prvku, jak je znázorněno v emulátoru Windows Phone.  
  
     ![Karta rozložení Průzkumníka modelu DOM](../debugger/media/js-css-layout.png "JS_CSS_Layout")  
  
     Toto zobrazení poskytuje některé užitečné informace o elementu:  
  
    - Barvy odpovídají zvýraznění pole, které se zobrazí v simulátoru při najetí myší na prvky. Modrá barva představuje \<img > prvků dimenzí. Barva Tan představuje hodnoty okrajů.  
  
    - Levý okraj (levý okraj) je nastaven, které Rady jsou v příčině problému, protože odpovídají příznaku (černé na levé straně obrázků).  
  
    - Pole, která zobrazují hodnoty 0 pixelů (například ohraničení a odsazení) naznačují, že pravděpodobně nejsou nastaveny odpovídající vlastnosti šablony stylů CSS.  
  
11. Chcete-li zjistit, jak je použito pravidlo pro levý okraj, vyberte **vypočítanou** kartu a podívejte se na pravidlo s levým okrajem. Můžete vidět, že toto pravidlo je nastavené s hodnotou 5em, ale vypočtená hodnota je buď 66.66 px, nebo 146.66 px, v závislosti na cílovém zařízení.  
  
    > [!TIP]
    > **Vypočítaná** karta ukazuje, že pravidlo levého horního okraje je nastaveno v selektoru `..hubpage .hub. section4 .sub-image-row img` šablon stylů CSS, nalezeno v centru. CSS. V této ukázkové aplikaci je potřeba provést opravu.  
  
     Můžete také použít kartu **rozložení** k testování úprav hodnot rozložení.  
  
12. Na kartě **rozložení** vyberte buď **66,66** nebo **146,66**, který se zobrazí v poli **okraj** na levé straně pole.  
  
13. Zadejte `0` a stiskněte Enter. (Můžete také změnit hodnotu pomocí kláves Šipka nahoru a šipka dolů.)  
  
14. V Průzkumníku modelu DOM vyberte jiné prvky \<img > a změňte jejich hodnoty vlevo na 0.  
  
15. Přepněte do emulátoru telefonu nebo simulátoru. Na obrázcích oddílu 4 byly aplikovány aktualizované hodnoty pro levý okraj. Tyto hodnoty se aktualizují také na kartě **vypočítané** v rámci pravidla marže na levé straně.  
  
## <a name="see-also"></a>Viz také  
 [Rychlý Start: ladění HTML a CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Ladění stylů CSS pomocí Průzkumníka modelu DOM](../debugger/debug-css-styles-using-dom-explorer.md)   
 [Zobrazení naslouchacích procesů událostí DOM](../debugger/view-dom-event-listeners.md)
