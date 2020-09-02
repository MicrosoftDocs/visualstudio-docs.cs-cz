---
title: Aktualizace aplikace (JavaScript) | Microsoft Docs
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
- JavaScript debugging, refreshing pages [Windows Store apps]
- debugging, refreshing pages [Windows Store apps]
- DOM Explorer, Refresh [Windows Store apps]
- Refresh [Windows Store apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b5b8be97212f4510002a78e6565fc9884930db89
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64808027"
---
# <a name="refresh-an-app-javascript"></a>Aktualizace aplikace (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Můžete provádět změny kódu během ladění a pak aktualizovat aplikaci ze Storu pomocí JavaScriptu tak, že kliknete na tlačítko **aktualizovat aplikaci pro Windows** na panelu nástrojů **ladění** . Kliknutím na toto tlačítko se aplikace znovu načte bez zastavení a restartování ladicího programu. Funkce aktualizovat umožňuje upravit kód HTML, CSS a JavaScript a rychle zobrazit výsledek. Tato funkce je podporovaná pro aplikace Windows Store i Windows Phone Store.  
  
 Aktualizace neudržuje stav aplikace nebo odráží následující změny vaší aplikace:  
  
- Změny souborů manifestu balíčku, včetně změn imagí zadaných v manifestu balíčku.  
  
- Referenční změny, jako je například přidání nebo odebrání odkazu na sadu SDK nebo změny prostředí Windows Runtimech komponent (soubory. winmd).  
  
- Změny prostředků, jako jsou například změny v řetězcích souborů. resjson.  
  
- Změny souborů projektu, které mají za následek změny názvu cesty, nové soubory projektu nebo odstraněné soubory.  
  
- Změny vlastností projektu a položky, jako jsou například změny vybraného ladicího zařízení, nebo změny pro akci balíčku pro soubor (v okno Vlastnosti).  
  
> [!IMPORTANT]
> Když změníte odkazy, změníte manifest balíčku nebo provedete jiné změny uvedené v předchozím seznamu, je nutné zastavit a znovu spustit ladicí program, aby bylo možné aktualizovat zdrojové soubory HTML, CSS a JavaScript.  
  
### <a name="to-refresh-an-app"></a>Aktualizace aplikace  
  
1. V aplikaci Visual Studio vytvořte nový projekt pomocí šablony projektu navigační aplikace.  
  
     Může to být aplikace pro Windows Store, aplikace Windows Phone Storu nebo univerzální aplikace.  
  
2. Otevřete šablonu v aplikaci Visual Studio a vyberte cíl ladění.  
  
     Pokud je projekt Windows Phone vaším aktuálním spouštěným projektem, vyberte Windows Phone emulátor pro cíl ladění. V opačném případě vyberte **simulátor** nebo **místní počítač**.  
  
     ![Vybrat cílový seznam pro ladění](../debugger/media/js-select-target.png "JS_Select_Target")  
  
3. Stisknutím klávesy F5 spusťte aplikaci v režimu ladění.  
  
4. Přepněte do sady Visual Studio. (Stiskněte klávesu F12.)  
  
5. V **Průzkumník řešení**na **pages**  >  **domovské** složce stránky otevřete home.html.  
  
6. Změnit text nadpisu stránky z  
  
    ```html  
    Welcome to yourAppName!  
    ```  
  
     do nějakého jiného, třeba takto:  
  
    ```html  
    Hello!  
    ```  
  
7. Klikněte na tlačítko **aktualizovat aplikaci pro Windows** , které vypadá takto: ![tlačítko Aktualizovat aplikaci pro Windows](../debugger/media/js-refresh.png "JS_Refresh"). (Nebo stiskněte F4.)  
  
8. Přepněte do aplikace. Aplikace se znovu načte bez restartování ladicího programu a zobrazí se nový název stránky.  
  
## <a name="see-also"></a>Viz také  
 [Rychlý start: Ladění kódu HTML a CSS](../debugger/quickstart-debug-html-and-css.md)
