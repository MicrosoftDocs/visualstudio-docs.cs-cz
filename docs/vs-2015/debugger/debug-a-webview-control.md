---
title: Ladění ovládacího prvku WebView | Dokumentace Microsoftu
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
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f8a4dcc64903b97e3b469fb962777e3b90f84ba
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729067"
---
# <a name="debug-a-webview-control"></a>Ladění ovládacího prvku WebView
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Ke kontrole a ladění `WebView` ovládací prvky v aplikaci Windows Runtime, můžete nakonfigurovat Visual Studio a připojit ladicí program skriptu při spuštění aplikace. Od verze Visual Studio 2013 Update 2, máte dva způsoby, jak pracovat s `WebView` ovládací prvky pomocí ladicího programu:  
  
-   Otevřít [Průzkumníka modelu DOM](../debugger/quickstart-debug-html-and-css.md) pro `WebView` instance a kontrole elementů modelu DOM, prozkoumat problémy stylu CSS a testovat dynamicky vykreslené změny stylů.  
  
-   Vyberte webovou stránku nebo `iFrame` zobrazí v `WebView` instance jako cíl v [konzoly jazyka JavaScript](../debugger/javascript-console-commands.md) okna a pak pracovat s webovou stránku pomocí příkazy konzoly. Konzole poskytuje přístup k aktuálním kontextu spuštění skriptu.  
  
### <a name="attach-the-debugger-c-visual-basic-c"></a>Připojit ladicí program (C#, Visual Basic, C++)  
  
1.  V sadě Visual Studio, přidejte `WebView` ovládacího prvku do aplikace pro Windows Runtime.  
  
2.  V Průzkumníku řešení otevřete vlastnosti projektu výběrem **vlastnosti** z místní nabídky pro projekt.  
  
3.  Zvolte **ladění**. V **proces aplikace** klikněte na položku **skript**.  
  
     ![Připojit ladicí program skriptu](../debugger/media/js-dom-webview-script-debugger.png "JS_DOM_WebView_Script_Debugger")  
  
4.  (Volitelné) Ne Express verzích sady Visual Studio se zakázat ladění just-in-time (JIT) výběrem **nástroje**, **možnosti**, **ladění**, **Just-In-Time**, a potom zakázat JIT ladění skriptu.  
  
    > [!NOTE]
    >  Zakázat ladění JIT, tak můžete skrýt dialogová okna neošetřených výjimek, ke kterým došlo u některých webových stránek. V aplikaci Visual Studio Express ladění JIT vždy zakázána.  
  
5.  Stisknutím klávesy F5 spusťte ladění.  
  
### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>Pomocí Průzkumníka modelu DOM ke kontrole a ladění ovládacího prvku WebView  
  
1.  (C#, Visual Basic, C++) Připojte ladicí program skriptu do vaší aplikace. Najdete v první části pokyny.  
  
2.  Pokud jste to ještě neudělali, přidejte `WebView` ovládací prvek do vaší aplikace a stisknutím klávesy F5 spusťte ladění.  
  
3.  Přejděte na stránku obsahující `Webview` ovládá.  
  
4.  Otevřete okno Průzkumníka modelu DOM `WebView` ovládací prvek výběrem **ladění**, **Windows**, **Průzkumníka modelu DOM**a pak zvolte adresu URL `WebView` , kterou jste Chcete zkontrolovat.  
  
     ![Otevření Průzkumníka modelu DOM](../debugger/media/js-dom-webview.png "JS_DOM_WebView")  
  
     V Průzkumníku modelu DOM přidružené `WebView` se zobrazí jako nová karta v sadě Visual Studio.  
  
5.  Zobrazit a upravit prvky živé DOM a stylů CSS, jak je popsáno v [styly ladění šablon stylů CSS pomocí Průzkumníka modelu DOM](../debugger/debug-css-styles-using-dom-explorer.md).  
  
### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>Použití okna konzoly jazyka JavaScript ke kontrole a ladění ovládacího prvku WebView  
  
1.  (C#, Visual Basic, C++) Připojte ladicí program skriptu do vaší aplikace. Najdete v první části pokyny.  
  
2.  Pokud jste to ještě neudělali, přidejte `WebView` ovládací prvek do vaší aplikace a stisknutím klávesy F5 spusťte ladění.  
  
3.  Otevřete okno konzoly jazyka JavaScript pro `WebView` ovládací prvek výběrem **ladění**, **Windows**, **konzoly jazyka JavaScript**.  
  
     Zobrazí se okno konzoly jazyka JavaScript.  
  
4.  Přejděte na stránku obsahující `Webview` ovládá.  
  
5.  V okně konzoly vyberte webovou stránku nebo `iFrame` zobrazený `WebView` v ovládacím prvku **cílové** seznamu.  
  
     ![Cílit na výběr v okně konzoly jazyka JavaScript](../debugger/media/js-console-target.png "JS_Console_Target")  
  
    > [!NOTE]
    >  Pomocí konzoly můžete pracovat s jedním `WebView`, `iFrame`, sdílet smlouvy nebo webového pracovního procesu v čase. Každý prvek vyžaduje samostatnou instanci hostitele webové platformy (WWAHost.exe). Najednou můžete pracovat s jednoho hostitele.  
  
6.  Zobrazení a úpravám proměnných ve vaší aplikaci nebo pomocí příkazů konzole, jak je popsáno v [rychlý start: ladění JavaScriptu](../debugger/quickstart-debug-javascript-using-the-console.md) a [příkazy konzoly jazyka JavaScript](../debugger/javascript-console-commands.md).  
  
## <a name="see-also"></a>Viz také  
 [Rychlý start: Ladění kódu HTML a CSS](../debugger/quickstart-debug-html-and-css.md)



