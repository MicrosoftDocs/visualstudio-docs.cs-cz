---
title: Ladění ovládacího prvku WebView (UWP) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: 8ba9b0eb17a492bf1912281038ffc35732ece96d
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72589072"
---
# <a name="debug-a-webview-control-in-a-uwp-app"></a>Ladění ovládacího prvku WebView v aplikaci UWP

 Chcete-li zkontrolovat a ladit `WebView` ovládací prvky v aplikaci prostředí Windows Runtime, můžete nakonfigurovat aplikaci Visual Studio tak, aby při spuštění aplikace připojila ladicí program skriptu. Existují dva způsoby, jak pracovat s ovládacími prvky `WebView` pomocí ladicího programu:

- Otevřete [Průzkumníka modelu DOM](../debugger/quickstart-debug-html-and-css.md) pro instanci `WebView` a prozkoumejte prvky modelu DOM, prozkoumejte problémy stylu CSS a otestujte dynamicky vykreslené změny stylů.

- Vyberte webovou stránku nebo `iFrame` zobrazenou v instanci `WebView` jako cíl v okně [konzoly JavaScriptu](../debugger/javascript-console-commands.md?view=vs-2017) a pak s webovou stránkou s použitím příkazů konzoly Pracujte interaktivně. Konzola poskytuje přístup k aktuálnímu kontextu spuštění skriptu.

### <a name="attach-the-debugger-c-visual-basic-c"></a>Připojit ladicí program (C#, Visual Basic, C++)

1. V aplikaci Visual Studio přidejte do aplikace prostředí Windows Runtime ovládací prvek `WebView`.

2. V Průzkumník řešení otevřete vlastnosti projektu výběrem **vlastnosti** z místní nabídky projektu.

3. Vyberte **ladit**. V seznamu **proces aplikace** vyberte možnost **skript**.

     ![Připojit ladicí program skriptu](../debugger/media/js_dom_webview_script_debugger.png "JS_DOM_WebView_Script_Debugger")

4. Volitelné Pro neexpresní verze sady Visual Studio zakažte ladění JIT (just-in-time), a to tak, že zvolíte **nástroje > možnosti > ladění > za běhu**a potom zakážete ladění JIT pro skript.

    > [!NOTE]
    > Zakázáním ladění JIT můžete skrýt dialogová okna pro neošetřené výjimky, ke kterým dochází na některých webových stránkách. V Visual Studio Express je ladění JIT vždy zakázáno.

5. Stisknutím klávesy F5 spusťte ladění.

### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>Kontrola a ladění ovládacího prvku WebView pomocí Průzkumníka modelu DOM

1. (C#, Visual Basic, C++) Připojte ladicí program skriptu k aplikaci. Pokyny najdete v první části.

2. Pokud jste to ještě neudělali, přidejte do aplikace ovládací prvek `WebView` a stisknutím klávesy F5 spusťte ladění.

3. Přejděte na stránku obsahující ovládací prvky `Webview`.

4. Otevřete okno Průzkumníka modelu DOM pro ovládací prvek `WebView` tak, že vyberete **ladit**, **Windows**, **Průzkumník modelu DOM**a pak zvolíte adresu URL `WebView`, kterou chcete zkontrolovat.

     ![Otevření Průzkumníka modelu DOM](../debugger/media/js_dom_webview.png "JS_DOM_WebView")

     Průzkumník modelu DOM, který je přidružený k `WebView`, se zobrazí jako nová karta v aplikaci Visual Studio.

5. Zobrazit a upravit prvky modelu DOM a styly CSS, jak je popsáno v tématu [Ladění stylů CSS pomocí Průzkumníka modelu DOM](/visualstudio/debugger/quickstart-debug-html-and-css).

### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>Kontrola a ladění ovládacího prvku WebView pomocí okna konzoly JavaScriptu

1. (C#, Visual Basic, C++) Připojte ladicí program skriptu k aplikaci. Pokyny najdete v první části.

2. Pokud jste to ještě neudělali, přidejte do aplikace ovládací prvek `WebView` a stisknutím klávesy F5 spusťte ladění.

3. Otevřete okno konzoly JavaScriptu pro ovládací prvek `WebView` tak, že vyberete **ladění**, **Windows**, **Konzola JavaScriptu**.

     Zobrazí se okno konzoly JavaScriptu.

4. Přejděte na stránku obsahující ovládací prvky `Webview`.

5. V okně konzoly vyberte webovou stránku nebo `iFrame` zobrazenou ovládacím prvkem `WebView` v seznamu **cílů** .

     ![Výběr cíle v okně konzoly JavaScriptu](../debugger/media/js_console_target.png "JS_Console_Target")

    > [!NOTE]
    > Pomocí konzoly nástroje můžete pracovat s jedním `WebView`, `iFrame`, sdílet smlouvu nebo webovým pracovníkem v jednom okamžiku. Každý prvek vyžaduje samostatnou instanci hostitele webové platformy (WWAHost. exe). Můžete komunikovat s jedním hostitelem současně.

6. Zobrazení a úprava proměnných ve vaší aplikaci nebo použití příkazů konzoly, jak je popsáno v tématu [rychlý Start: ladění](../debugger/quickstart-debug-javascript-using-the-console.md) [příkazů konzoly](../debugger/javascript-console-commands.md?view=vs-2017)JavaScript a JavaScript.

## <a name="see-also"></a>Viz také

- [Rychlý start: Ladění kódu HTML a CSS](../debugger/quickstart-debug-html-and-css.md)