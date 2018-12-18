---
title: Analýza programových testů uživatelského rozhraní pomocí protokolů z těchto testů
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 9c31dd90981cf39f1de296b2c96d6064afc730b4
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896676"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Analýza kódované UI testy pomocí programového protokolů testu uživatelského rozhraní

Programového uživatelského rozhraní testu protokoly filtr a záznam, který běží důležité informace o programového testu UI. Protokoly jsou uvedeny ve formátu, který umožňuje ladění problémů rychle.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="step-1-enable-logging"></a>Krok 1: Povolení protokolování

V závislosti na scénáři použijte jednu z následujících metod k povolení protokolu:

- Cílit na rozhraní .NET Framework verze 4 bez *App.config* soubor v projektu testu:

   1. Otevřít *QTAgent32_40.exe.config* souboru. Ve výchozím nastavení je tento soubor umístěn ve *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

   2. Upravte hodnotu EqtTraceLevel na požadovanou úroveň protokolu.

   3. Uložte soubor.

- Cílit na rozhraní .NET Framework verze 4.5 bez *App.config* soubor v projektu testu:

   1. Otevřít *QTAgent32.exe.config* souboru. Ve výchozím nastavení je tento soubor umístěn ve *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

   2. Upravte hodnotu EqtTraceLevel na požadovanou úroveň protokolu.

   3. Uložte soubor.

- *App.config* soubor je k dispozici v projektu testu:

    - Otevřít *App.config* souboru v projektu a přidejte následující kód v uzlu Konfigurace:

      ```xml
      <system.diagnostics>
        <switches>
          <add name="EqtTraceLevel" value="4" />
        </switches>
      </system.diagnostics>`
      ```

- Povolení protokolování z samotný kód testu:

   <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState%2A> = HtmlLoggerState.AllActionSnapshot;

## <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>Krok 2: Spuštění programového testu uživatelského rozhraní a zobrazit protokol

Při spuštění programového testu uživatelského rozhraní pomocí změny *QTAgent32.exe.config* soubor na místě, zobrazí se výstup na odkaz v **Průzkumníka testů** výsledky. Soubory protokolů jsou vytvářeny, ne jenom v případě, že se test nezdaří, ale také u úspěšných testů, pokud je úroveň trasování nastavena na "podrobné."

1.  Na **testovací** nabídce zvolte **Windows** a pak vyberte **Průzkumník testů**.

2.  Na **sestavení** nabídce zvolte **sestavit řešení**.

3.  V **Průzkumníka testů**, vyberte programový test uživatelského rozhraní, kterou chcete spustit, otevřete místní nabídku a klikněte na tlačítko **spustit vyberte testy**.

     Automatizované testy proběhnou a označení pokud úspěšný nebo neúspěšný.

    > [!TIP]
    > Chcete-li zobrazit **Průzkumník testů**, zvolte **testovací** > **Windows**a klikněte na tlačítko **Průzkumník testů**.

4.  Zvolte **výstup** odkaz v **Průzkumník testů** výsledky.

     ![Výstup odkaz v Průzkumníku testů](../test/media/cuit_htmlactionlog1.png)

     Zobrazí se výstup pro test, který obsahuje odkaz na protokol akcí.

     ![Výsledky a odkazy na výstup z programového testu uživatelského rozhraní](../test/media/cuit_htmlactionlog2.png)

5.  Zvolte *UITestActionLog.html* odkaz.

     Protokol se zobrazí ve webovém prohlížeči.

     ![Programový soubor protokolu testu uživatelského rozhraní](../test/media/cuit_htmlactionlog3.png)

## <a name="see-also"></a>Viz také:

- [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)
- [Postupy: spuštění testů ze sady Microsoft Visual Studio](https://msdn.microsoft.com/Library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)