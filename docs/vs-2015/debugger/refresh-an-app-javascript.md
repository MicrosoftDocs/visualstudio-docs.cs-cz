---
title: Aktualizace aplikace (JavaScript) | Dokumentace Microsoftu
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
- JavaScript debugging, refreshing pages [Windows Store apps]
- debugging, refreshing pages [Windows Store apps]
- DOM Explorer, Refresh [Windows Store apps]
- Refresh [Windows Store apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1905d48e79567684da6215b419c348b32721e0e3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722893"
---
# <a name="refresh-an-app-javascript"></a>Aktualizace aplikace (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Můžete provedete změny kódu během ladění a pak aktualizujte Store app pomocí jazyka JavaScript výběrem **aktualizovat Windows app** tlačítko **ladění** nástrojů. Výběrem tohoto tlačítka znovu načte aplikace bez zastavení a restartování ladicího programu. Funkce aktualizace umožňuje upravit kód HTML, CSS a JavaScriptu a rychle zobrazit výsledek. Tato funkce je podporována pro aplikace pro Windows Store a Windows Phone Store.  
  
 Aktualizaci nelze udržovat stav vaší aplikace nebo zahrnují následující změny do vaší aplikace:  
  
-   Změny souboru manifestu balíčku, včetně změn imagí v manifestu balíčku.  
  
-   Odkaz na změny, jako je například přidávání nebo odebírání odkaz na sadu SDK nebo změny součástí prostředí Windows Runtime (soubory .winmd).  
  
-   Změny zdrojů, jako jsou například změny v souborech .resjson řetězce.  
  
-   Soubor projektu se změní výsledek ve změně názvu cesty, nové soubory projektu nebo odstraněné soubory.  
  
-   Projektů a položek změny vlastností, jako jsou například změny vybrané ladění zařízení, nebo změny akce balíčku souboru (v okně Vlastnosti).  
  
> [!IMPORTANT]
>  Pokud změníte odkazy, změňte manifest balíčku nebo provést další změny, které uvedli v předchozím seznamu, budete muset zastavit a restartovat ladicí program k aktualizaci zdrojové soubory HTML, CSS a JavaScriptu.  
  
### <a name="to-refresh-an-app"></a>Chcete-li aktualizovat aplikaci  
  
1.  V sadě Visual Studio vytvořte nový projekt pomocí šablony projektu aplikace navigace.  
  
     To může být aplikace Windows Store, app Store pro Windows Phone nebo univerzální aplikace.  
  
2.  Pomocí šablony otevřete v sadě Visual Studio, vyberte cíl ladění.  
  
     Pokud je projekt Windows Phone aktuální spouštěcí projekt, vyberte emulátor Windows Phone pro cíl ladění. V opačném případě vyberte **simulátor** nebo **místního počítače**.  
  
     ![Seznam cílů ladění vyberte](../debugger/media/js-select-target.png "JS_Select_Target")  
  
3.  Stisknutím klávesy F5 spusťte aplikaci v režimu ladění.  
  
4.  Přepněte do aplikace Visual Studio. (Stiskněte klávesu F12).  
  
5.  V **Průzkumníka řešení**v **stránky** > **domácí** složku, otevřete home.html.  
  
6.  Změnit text nadpisu stránky z  
  
    ```html  
    Welcome to yourAppName!  
    ```  
  
     na něco jiného, například takto:  
  
    ```html  
    Hello!  
    ```  
  
7.  Klikněte na tlačítko **aktualizovat Windows app** tlačítka, která vypadá přibližně takto: ![tlačítko Aktualizovat Windows app](../debugger/media/js-refresh.png "JS_Refresh"). (Nebo stisknutím klávesy F4).  
  
8.  Přepněte do aplikace. Aplikace opětovném načtení nástroje bez ladicího programu, restartování a zobrazí se nový název stránky.  
  
## <a name="see-also"></a>Viz také  
 [Rychlý start: Ladění kódu HTML a CSS](../debugger/quickstart-debug-html-and-css.md)



