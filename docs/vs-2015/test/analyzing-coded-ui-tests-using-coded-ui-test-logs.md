---
title: Analýza programových testů uživatelského rozhraní pomocí protokolů kódovaného testu uživatelského rozhraní | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 7e795873-1d4b-4a13-a52a-a411d87fb759
caps.latest.revision: 15
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d3ebb18aaff78d9782b6210e25bcd697d21c8570
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660769"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Analýza programových testů uživatelského rozhraní pomocí protokolů z těchto testů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Protokoly programových testů uživatelského rozhraní filtr a zaznamenávají důležité informace o běhu programového testu uživatelského rozhraní.

 **Požadavky**

- Visual Studio Enterprise

## <a name="why-should-i-do-this"></a>Proč to mám udělat?
 Protokoly se zobrazí ve formátu, který umožňuje rychle ladit problémy.

## <a name="how-do-i-do-this"></a>Návody to udělat?

### <a name="step-1-enable-logging"></a>Krok 1: povolení protokolování
 V závislosti na vašem scénáři použijte k povolení protokolu jednu z následujících metod.

- V testovacím projektu neexistuje cílový .NET Framework verze 4 bez souboru App. config.

  - Otevřete soubor **QTAgent32_40. exe. config** .

    Ve výchozím nastavení je tento soubor umístěný ve složce **\<drvie >: \Program Files (x86) \Microsoft Visual Studio 12.0 \ Common7\IDE**.

    Změňte hodnotu EqtTraceLevel na úroveň protokolu, kterou chcete.

    Uložte soubor.

- V testovacím projektu není k dispozici cílový .NET Framework verze 4,5 bez souboru App. config.

  - Otevřete soubor **QTAgent32. exe. config** .

    Ve výchozím nastavení je tento soubor umístěný ve složce **\<drvie >: \Program Files (x86) \Microsoft Visual Studio 12.0 \ Common7\IDE**.

    Upravte hodnotu EqtTraceLevel na úroveň protokolu, kterou chcete.

    Uložte soubor.

- Soubor App. config přítomen v projektu testu

  - Otevřete soubor App. config v projektu.

    Do uzlu Konfigurace přidejte následující kód:

    `<system.diagnostics>     <switches>       <add name="EqtTraceLevel" value="4" />     </switches>  </system.diagnostics>`

- Povolit protokolování z samotného testovacího kódu

  - <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState%2A> = HtmlLoggerState. AllActionSnapshot;

### <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>Krok 2: spuštění kódovaného testu uživatelského rozhraní a zobrazení protokolu
 Když spustíte programový test UI s úpravami v souboru **QTAgent32. exe. config** , uvidíte, že v Průzkumníku testů je odkaz na výstup. Soubory protokolu se vytvářejí nejen v případě, že test selhává, ale také pro úspěšné testy, pokud je úroveň trasování nastavená na Verbose.

1. V nabídce **test** zvolte **okna** a pak vyberte **Průzkumník testů**.

2. V nabídce **sestavení** klikněte na příkaz **Sestavit řešení**.

3. V Průzkumníku testů vyberte programový test UI, který chcete spustit, otevřete místní nabídku a zvolte možnost **Spustit výběr testů**.

     Automatizované testy se spustí a určí, jestli byly úspěšné nebo neúspěšné.

    > [!TIP]
    > Chcete-li zobrazit Průzkumníka testů z **nabídky test**, přejděte na příkaz **Windows** a pak zvolte možnost **Průzkumník testů**.

4. Vyberte odkaz **výstup** ve výsledcích Průzkumníka testů.

     ![Odkaz na výstup v Průzkumníku testů](../test/media/cuit-htmlactionlog1.png "CUIT_HTMLActionLog1")

     Tím se zobrazí výstup testu, který bude obsahovat odkaz na protokol akcí.

     ![Odkazy na výsledky a výstupy ze kódovaného testu uživatelského rozhraní](../test/media/cuit-htmlactionlog2.png "CUIT_HTMLActionLog2")

5. Vyberte odkaz UITestActionLog. html.

     Protokol se zobrazí ve webovém prohlížeči.

     ![Soubor protokolu programového testu UI](../test/media/cuit-htmlactionlog3.png "CUIT_HTMLActionLog3")

## <a name="q--a"></a>Otázka & A

### <a name="q-what-happened-to-the-enablehtmllogger-key"></a>Otázka: co se stalo s EnableHtmlLogger klíčem?
 V předchozích verzích sady Visual Studio existovalo dvě další nastavení konfigurace pro povolení protokolovacího nástroje HTML v programovém testu uživatelského rozhraní:

```

<add key="EnableHtmlLogger" value="true"/>

<add key="EnableSnapshotInfo" value="true"/>

```

 Obě tato nastavení se od sady Visual Studio 2012 už nepoužívá. EqtTraceLevel je jediné nastavení, které je potřeba upravit, aby se povolilo HtmlLogger.

## <a name="see-also"></a>Viz také
 [Použití automatizace uživatelského rozhraní k otestování kódu](../test/use-ui-automation-to-test-your-code.md) [Postupy: spuštění testů z Microsoft Visual Studio](https://msdn.microsoft.com/library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)
