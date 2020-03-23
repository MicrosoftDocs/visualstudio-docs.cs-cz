---
title: Analýza programových testů uživatelského rozhraní pomocí protokolů z těchto testů
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: ec1025eaa53861fae2cf92395d8842854649fa8c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591213"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Analýza kódovaných testů ui pomocí kódovaných protokolů testů ui

Protokoly testovaných kódovaných ui filtrují a zaznamenávají důležité informace o spuštění chutovaných testovacích běhů ui. Protokoly jsou uvedeny ve formátu, který umožňuje problémy ladění rychle.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="step-1-enable-logging"></a>Krok 1: Povolení protokolování

V závislosti na scénáři povolte protokol jednou z následujících metod:

- Pokud v testovacím projektu není žádný soubor *App.config:*

   1. Zjistěte, který proces *QTAgent\*.exe* je spuštěn při spuštění testu. Jedním ze způsobů, jak to provést, je sledovat kartu **Podrobnosti** ve **Správci úloh systému**Windows .

   2. Otevřete odpovídající soubor *.config* ze složky *%ProgramFiles(x86)%\Microsoft Visual Studio\\\<verze>\\ \<edition>\Common7\IDE.* Pokud je například spuštěný proces *QTAgent_40.exe*, otevřete *soubor QTAgent_40.exe.config*.

   2. Upravte hodnotu **EqtTraceLevel** na požadovanou úroveň protokolu.

      ```xml
      <!-- You must use integral values for "value".
           Use 0 for off, 1 for error, 2 for warn, 3 for info, and 4 for verbose. -->
      <add name="EqtTraceLevel" value="4" />
      ```

   3. Uložte soubor.

- Pokud je v testovacím projektu přítomen soubor *App.config:*

  - Otevřete soubor *App.config* v projektu a pod konfigurační uzel přidejte následující kód:

    ```xml
    <system.diagnostics>
      <switches>
        <add name="EqtTraceLevel" value="4" />
      </switches>
    </system.diagnostics>`
    ```

- Povolit protokolování ze samotného testovacího kódu:

   ```csharp
   Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState = HtmlLoggerState.AllActionSnapshot;
   ```

## <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>Krok 2: Spuštění programového testu ui a zobrazení protokolu

Při spuštění programového testu ui s úpravami souboru *QTAgent\*.exe.config* na místě se zobrazí výstupní odkaz ve výsledcích **Průzkumníka testů.** Soubory protokolu jsou vyráběny nejen v případě, že váš test selže, ale také pro úspěšné testy, pokud je úroveň trasování **nastavena**na podrobné .

1. V nabídce **Test** zvolte **Windows** a pak vyberte **Průzkumník a test**.

2. V nabídce **Build** zvolte **Build Solution**.

3. V **Průzkumníkovi testů**vyberte kódovaný test ui, který chcete spustit, otevřete jeho místní nabídku a pak zvolte **Spustit testy výběru**.

     Automatizované testy spustit a určit, pokud byly předány nebo se nezdařilo.

    > [!TIP]
    > Chcete-li zobrazit **Průzkumníka testů**, zvolte **Testovat** > **windows**a pak zvolte Test **Explorer**.

4. Ve výsledcích **Průzkumníka testů** zvolte odkaz **Výstup.**

     ![Odkaz na výstup v Průzkumníku testů](../test/media/cuit_htmlactionlog1.png)

     Zobrazí se výstup pro test, který obsahuje odkaz na protokol akcí.

     ![Výsledky a výstupní odkazy z kódovaného testu ui](../test/media/cuit_htmlactionlog2.png)

5. Zvolte odkaz *UITestActionLog.html.*

     Protokol se zobrazí ve webovém prohlížeči.

     ![Kódovaný soubor protokolu testovacího ui](../test/media/cuit_htmlactionlog3.png)

## <a name="see-also"></a>Viz také

- [Testování kódu pomocí automatizace uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md)
- [Postup: Spuštění testů z aplikace Microsoft Visual Studio](https://msdn.microsoft.com/Library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)
