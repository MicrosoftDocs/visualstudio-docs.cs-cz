---
title: Ladění ovládacího prvku webového zobrazení (UWP) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 4576cfa5724869aba86842c5debb4df685559879
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31465457"
---
# <a name="debug-a-webview-control-in-a-uwp-app"></a>Ladění ovládacího prvku webového zobrazení v aplikaci UWP
  
 Zkontrolujte a ladit `WebView` ovládacích prvků v prostředí Windows Runtime aplikace, můžete nakonfigurovat Visual Studio se připojit ladicí program skriptu, při spuštění aplikace. Máte dva způsoby, jak pracovat s `WebView` řídí používání ladicího programu:  
  
-   Otevřete [Průzkumníka modelu DOM](../debugger/quickstart-debug-html-and-css.md) pro `WebView` instance a zkontrolujte elementů modelu DOM, prozkoumat problémy stylu CSS a testování dynamicky vykreslené změny stylů.  
  
-   Vyberte webovou stránku nebo `iFrame` zobrazí v `WebView` instance jako cíl v [konzoly pro JavaScript](../debugger/javascript-console-commands.md) okno a poté musí komunikovat s webovou stránku pomocí příkazů konzole. Konzole poskytuje přístup k aktuálním kontextu spuštění skriptu.  
  
### <a name="attach-the-debugger-c-visual-basic-c"></a>Připojit ladicí program (C# a Visual Basic, C++)  
  
1.  V sadě Visual Studio, přidejte `WebView` ovládacího prvku do aplikace Windows Runtime.  
  
2.  V Průzkumníku řešení otevřete vlastnosti pro projekt tak, že zvolíte **vlastnosti** z místní nabídky projektu.  
  
3.  Zvolte **ladění**. V **proces aplikace** vyberte **skriptu**.  
  
     ![Připojit ladicí program skriptu](../debugger/media/js_dom_webview_script_debugger.png "JS_DOM_WebView_Script_Debugger")  
  
4.  (Volitelné) Pro jiný expresní verze sady Visual Studio, zakažte v běhu (JIT) ladění výběrem **nástroje > Možnosti > ladění > těsně za běhu**, a pak zakázání JIT ladění skriptu.  
  
    > [!NOTE]
    >  Zakázáním ladění JIT můžete skrýt, dialogová okna pro neošetřených výjimek, ke kterým došlo u některých webových stránek. V aplikaci Visual Studio Express JIT je vždy zakázat ladění.  
  
5.  Stisknutím klávesy F5 spusťte ladění.  
  
### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>Pomocí Průzkumníka modelu DOM ke kontrole a ladění ovládacího prvku webového zobrazení  
  
1.  (C# a Visual Basic, C++) Připojte ladicí program skriptu do vaší aplikace. Najdete v první části pokyny.  
  
2.  Pokud jste to ještě neudělali, přidejte `WebView` řízení do vaší aplikace a stisknutím klávesy F5 spusťte ladění.  
  
3.  Přejděte na stránku obsahující `Webview` ovládá.  
  
4.  Otevřete okno Průzkumníka modelu DOM pro `WebView` ovládacího prvku tak, že zvolíte **ladění**, **Windows**, **Průzkumníka modelu DOM**a potom vyberte adresu URL `WebView` , které chcete prověřit.  
  
     ![Otevření Průzkumníka modelu DOM](../debugger/media/js_dom_webview.png "JS_DOM_WebView")  
  
     Průzkumník modelu DOM přidružené `WebView` se zobrazí jako novou kartu v sadě Visual Studio.  
  
5.  Zobrazení a změna za provozu elementů modelu DOM a stylů CSS, jak je popsáno v [styly ladění šablon stylů CSS pomocí Průzkumníka modelu DOM](../debugger/debug-css-styles-using-dom-explorer.md).  
  
### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>Použití okna konzoly jazyka JavaScript ke kontrole a ladění ovládacího prvku webového zobrazení  
  
1.  (C# a Visual Basic, C++) Připojte ladicí program skriptu do vaší aplikace. Najdete v první části pokyny.  
  
2.  Pokud jste to ještě neudělali, přidejte `WebView` řízení do vaší aplikace a stisknutím klávesy F5 spusťte ladění.  
  
3.  Otevřete okno konzoly pro JavaScript pro `WebView` ovládacího prvku tak, že zvolíte **ladění**, **Windows**, **konzoly pro JavaScript**.  
  
     Zobrazí se okno konzoly pro JavaScript.  
  
4.  Přejděte na stránku obsahující `Webview` ovládá.  
  
5.  V okně konzoly vyberte webovou stránku nebo `iFrame` zobrazuje `WebView` řídit ve **cíl** seznamu.  
  
     ![Cíl výběr v okně konzoly jazyka JavaScript](../debugger/media/js_console_target.png "JS_Console_Target")  
  
    > [!NOTE]
    >  Pomocí konzoly, můžete pracovat s jedním `WebView`, `iFrame`, sdílet kontrakt nebo web pracovního procesu v čase. Každý prvek vyžaduje samostatnou instanci hostitele webové platformy (WWAHost.exe). Najednou můžete pracovat s jednoho hostitele.  
  
6.  Zobrazení a úpravám proměnných v aplikaci nebo pomocí příkazů konzole, jak je popsáno v [rychlý úvod: ladění JavaScriptu](../debugger/quickstart-debug-javascript-using-the-console.md) a [příkazy konzoly pro JavaScript](../debugger/javascript-console-commands.md).  
  
## <a name="see-also"></a>Viz také  
 [Rychlý úvod: Ladění kódu HTML a CSS](../debugger/quickstart-debug-html-and-css.md)