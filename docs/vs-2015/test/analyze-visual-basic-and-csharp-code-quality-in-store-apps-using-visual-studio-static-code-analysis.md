---
title: Analýza kódu Visual Basic a C# v aplikacích pro Store pomocí statické analýzy kódu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb.express
ms.assetid: cab553fc-19a9-4cbf-858e-8200258ffe50
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cfe5ed57bfc361b711ed2aceceff2aabfc44cf4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660741"
---
# <a name="analyze-visual-basic-and-c-code-quality-in-store-apps-using-visual-studio-static-code-analysis"></a>Analýza kódu Visual Basic a C# v aplikacích pro Store pomocí statické analýzy kódu sady Visual Studio

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Nástroj Analýza kódu v Visual Studio Express kontroluje váš kód pro sadu běžných vad a porušení dobrého programovacího postupu. Upozornění analýzy kódu se liší od chyb kompilátoru a upozornění, protože nástroj pro analýzu kódu vyhledává konkrétní vzor kódu, který je platný, ale může stále vytvářet problémy pro vás nebo jiné uživatele, kteří používají váš kód. Analýza kódu může také najít vady v kódu, které se obtížně zjišťují prostřednictvím testování. Spuštění nástroje Code Analysis v pravidelných intervalech během procesu vývoje může zlepšit kvalitu dokončené aplikace.

> [!NOTE]
> V Visual Studio Ultimate, Visual Studio Premium a Visual Studio Professional, můžete použít plnou funkčnost nástroje Code Analysis. Viz [Analýza kvality aplikace pomocí nástrojů pro analýzu kódu](https://msdn.microsoft.com/library/dd264897.aspx) v knihovně MSDN.

## <a name="in-this-topic"></a>V tomto tématu
 Můžete se dozvědět:

 [Spuštění analýzy kódu](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Run)

 [Analýza a řešení upozornění analýzy kódu](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Analyze)

 [Potlačení upozornění analýzy kódu](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Suppress)

 [Hledání a filtrování výsledků analýzy kódu](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Search)

 [Upozornění analýzy kódu Visual Basic a C#](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Warnings)

## <a name="running-code-analysis"></a><a name="BKMK_Run"></a> Spuštění analýzy kódu
 Spuštění analýzy kódu v řešení sady Visual Studio:

- V nabídce **sestavení** vyberte možnost **Spustit analýzu kódu v řešení**.

  Chcete-li automaticky spustit analýzu kódu při každém sestavení projektu:

1. Klikněte pravým tlačítkem myši na název projektu v Průzkumník řešení a zvolte možnost **vlastnosti**.

2. Na stránce vlastností projektu zvolte možnost **Analýza kódu** a pak zvolte možnost **Povolit analýzu kódu při sestavení (definuje konstantu CodeAnalysis)**.

   Řešení se zkompiluje a spustí se analýza kódu. Výsledky se zobrazí v okně Analýza kódu.

   ![Okno Analýza kódu](../test/media/ca-managed-collapsed.png "CA_Managed_Collapsed")

## <a name="analyzing-and-resolving-code-analysis-warnings"></a><a name="BKMK_Analyze"></a> Analýza a řešení upozornění analýzy kódu
 Chcete-li analyzovat konkrétní upozornění, klikněte na název upozornění v okně Analýza kódu. Upozornění se rozbalí, aby se zobrazily podrobné informace o problému.

 ![Upozornění analýzy rozbaleného kódu](../test/media/ca-managed-callouts.png "CA_Managed_Callouts")

 Když rozbalíte upozornění, zvýrazní se řádek kódu, který způsobil upozornění, v editoru kódu sady Visual Studio.

 ![Zvýraznění textu analýzy kódu](../test/media/ca-managed-sourceline.png "CA_Managed_SourceLine")

 Po pochopení problému ho můžete vyřešit ve svém kódu. Pak znovu spusťte analýzu kódu, abyste se ujistili, že se upozornění již nebude zobrazovat v okně analýzy kódu a že oprava nevyvolala nová upozornění.

> [!TIP]
> Můžete znovu spustit analýzu kódu z okna Analýza kódu. Klikněte na tlačítko **analyzovat** a vyberte rozsah analýzy. Analýzu můžete znovu spustit pro celé řešení nebo na vybraný projekt.

## <a name="suppressing-code-analysis-warnings"></a><a name="BKMK_Suppress"></a> Potlačení upozornění analýzy kódu
 Existují situace, kdy se můžete rozhodnout, že nechcete opravit upozornění analýzy kódu. Můžete se rozhodnout, že vyřešení upozornění vyžaduje příliš mnoho překódování ve vztahu k pravděpodobnosti, že problém nastane v jakékoli implementaci kódu reálného světa. Nebo se můžete domnívat, že analýza, která se používá v upozornění, je pro konkrétní kontext nevhodná. Můžete potlačit jednotlivá upozornění, aby se již nezobrazovala v okně Analýza kódu.

 Chcete-li potlačit upozornění:

1. Pokud se podrobné informace nezobrazí, klikněte na název upozornění a rozbalte ho.

2. V dolní části upozornění klikněte na odkaz **Akce** .

3. Ukažte na **potlačit zprávu** a pak zvolte buď **ve zdroji** , nebo **v souboru potlačení**.

   - **Ve zdroji** vloží `SuppressMessage` atribut ve zdrojovém souboru nad metodu, která vygenerovala upozornění. To usnadňuje potlačení.

   - **V souboru potlačení** přidá `SuppressMessage` atribut do souboru **GlobalSuppressions.cs** projektu. To může usnadnit správu potlačení. Všimněte si, že `SuppressMessage` atribut přidaný do **GlobalSuppression.cs** také cílí na metodu, která vygenerovala upozornění. Potlačí upozornění globálně.

     Vaše rozhodnutí, jestli se má potlačit upozornění ve zdrojovém souboru nebo v souboru potlačení, závisí na stylu a potřebách kódování.

## <a name="searching-and-filtering-code-analysis-results"></a><a name="BKMK_Search"></a> Hledání a filtrování výsledků analýzy kódu
 Můžete vyhledávat dlouhé seznamy varovných zpráv a můžete filtrovat upozornění v řešeních s více projekty.

 ![Hledání a filtrování okna Analýza kódu](../test/media/ca-searchfilter.png "CA_SearchFilter")

 V nástroji [!INCLUDE[vs_dev11_expwin_long](../includes/vs-dev11-expwin-long-md.md)] mají všechna upozornění analýzy kódu úroveň závažnosti upozornění.

## <a name="visual-basic-and-c-code-analysis-warnings"></a><a name="BKMK_Warnings"></a> Upozornění analýzy kódu Visual Basic a C#
 Analýza kódu vyvolá následující upozornění:

 [CA1001: Typy, které vlastní uvolnitelné pole, by měly být uvolnitelné](https://msdn.microsoft.com/library/ms182172.aspx)

 [CA1821: Odeberte prázdné finalizační metody](https://msdn.microsoft.com/library/bb264476.aspx)

 [CA2213: Uvolnitelná pole by měla být uvolněna](https://msdn.microsoft.com/library/ms182328.aspx)

 [CA2229: Implementujte serializační konstruktory](https://msdn.microsoft.com/library/ms182343.aspx)

 [CA2231: Přetižte operátor rovnosti při přetížení ValueType.Equals](https://msdn.microsoft.com/library/ms182359.aspx)
