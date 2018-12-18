---
title: Analýza jazyka Visual Basic a C# kódu kvality v aplikacích pro Store pomocí statické analýzy kódu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb.express
ms.assetid: cab553fc-19a9-4cbf-858e-8200258ffe50
caps.latest.revision: 16
author: erickson-doug
ms.author: gewarren
manager: douge
ms.openlocfilehash: a3a3d753f9e2dd3b046159d191149b7af062fe16
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063205"
---
# <a name="analyze-visual-basic-and-c-code-quality-in-store-apps-using-visual-studio-static-code-analysis"></a>Analýza kvality kódu jazyka Visual Basic a C# v aplikacích pro Store pomocí sady Visual Studio statické analýzy kódu

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Nástroj pro analýzu kódu v sadě Visual Studio Express prozkoumá váš kód pro sadu běžné závady a porušování programovacím vhodné. Upozornění analýzy kódu se liší od kompilátoru chyby a upozornění, protože nástroj pro analýzu kódu hledá vzory v konkrétním kódu, které jsou platné, ale přesto vytvořit problémy pro vy nebo ostatní uživatelé, kteří používají váš kód. Analýzy kódu můžete také vyhledat chyby v kódu, které je obtížné vyhledat pomocí testování. Spuštění nástroje Analýza kódu v pravidelných intervalech během procesu vývoje můžete zvýšit tak kvalitu dokončené aplikace.

> [!NOTE]
>  V sadě Visual Studio Ultimate, Visual Studio Premium a Visual Studio Professional můžete použít všechny funkce pro analýzu kódu. Zobrazit [analýza kvality aplikace pomocí nástrojů pro analýzu kódu](http://msdn.microsoft.com/library/dd264897.aspx) v knihovně MSDN.

## <a name="in-this-topic"></a>V tomto tématu
 Informace o:

 [Spuštění analýzy kódu](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Run)

 [Analýza a řešení upozornění analýzy kódu](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Analyze)

 [Potlačení upozornění analýzy kódu](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Suppress)

 [Vyhledávání a filtrování výsledků analýzy kódu](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Search)

 [Upozornění analýzy kódu jazyka Visual Basic a C#](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Warnings)

##  <a name="BKMK_Run"></a> Spuštění analýzy kódu
 Spuštění analýzy kódu pro řešení sady Visual Studio:

- Na **sestavení** nabídce zvolte **spustit analýzu kódu na řešení**.

  Automaticky spustit analýzu kódu pokaždé, když vytváříte projekt:

1. Klikněte pravým tlačítkem na název projektu v Průzkumníku řešení a klikněte na tlačítko **vlastnosti**.

2. Na stránce vlastností projektu zvolte **analýzy kódu** a klikněte na tlačítko **povolit analýzu kódu na sestavení (definuje konstantu úloze CODEANALYSIS)**.

   Toto řešení je zkompilován a spuštění analýzy kódu. Výsledky se zobrazí v okně analýzy kódu.

   ![Okno Analýza kódu](../test/media/ca-managed-collapsed.png "CA_Managed_Collapsed")

##  <a name="BKMK_Analyze"></a> Analýza a řešení upozornění analýzy kódu
 Pokud chcete analyzovat konkrétního upozornění, klikněte na název upozornění v okně analýzy kódu. Upozornění se rozbalí a zobrazí podrobné informace o problému.

 ![Upozornění analýzy kódu pro rozbalení](../test/media/ca-managed-callouts.png "CA_Managed_Callouts")

 Při rozšiřování upozornění na řádek kódu, který způsobil toto upozornění je zvýrazněn v editoru kódu sady Visual Studio.

 ![Code analysis zvýraznění textu](../test/media/ca-managed-sourceline.png "CA_Managed_SourceLine")

 Po zjištění problému ho mohli vyřešit ve vašem kódu. Pak znovu spusťte analýzu kódu, abyste měli jistotu, že již nezobrazuje upozornění v okně analýzy kódu, a nová upozornění, že jste kód opravili správně nebyla vyvolána.

> [!TIP]
>  Můžete znovu spustit analýzu kódu v okně analýzy kódu. Klikněte na tlačítko **analyzovat** tlačítko a zvolte obor analýzy. Můžete znovu spustit analýzu na celé řešení nebo vybraný projekt.

##  <a name="BKMK_Suppress"></a> Potlačení upozornění analýzy kódu
 Existují situace, kdy byste se mohli rozhodnot Neopravovat upozornění analýzy kódu. Můžete se rozhodnout, že řešení upozornění vyžaduje příliš mnoho nahrávání ve vztahu k pravděpodobnost, že problém vzniknou v žádné Skutečná implementace kódu. Nebo může domnívat, že je nevhodná pro konkrétní kontext, který se používá v tomto upozornění analýzy. Jednotlivá upozornění můžete potlačit tak, aby se nebude zobrazovat v okně analýzy kódu.

 Chcete-li potlačit upozornění:

1. Pokud se zobrazí podrobné informace, klikněte na název upozornění a rozbalte ho.

2. Zvolte **akce** odkaz v dolní části upozornění.

3. Přejděte na **potlačit zprávu** a zvolte buď **zdroje v** nebo **v souboru potlačení**.

   - **Ve zdroji** vloží `SuppressMessage` atributů ve zdrojovém souboru nad metodami, které upozornění vygenerovalo. Díky tomu potlačení bude lepší dostupnost.

   - **V souboru potlačení** přidá `SuppressMessage` atribut **GlobalSuppressions.cs** souboru projektu. To může usnadnit správu potlačení. Všimněte si, že `SuppressMessage` atribut přidán do **GlobalSuppression.cs** také cílí na metodu, která vygeneruje upozornění. Nepotlačuje upozornění globálně.

     Vaše rozhodnutí, jestli se má potlačit upozornění ve zdrojovém souboru nebo v souboru potlačení závisí na styl psaní kódu a potřebám.

##  <a name="BKMK_Search"></a> Vyhledávání a filtrování výsledků analýzy kódu
 Můžete hledat dlouhé seznamy varovné zprávy a upozornění v řešení vícenásobného projektu můžete filtrovat.

 ![Hledání a filtrování v okně analýzy kódu](../test/media/ca-searchfilter.png "CA_SearchFilter")

 V [!INCLUDE[vs_dev11_expwin_long](../includes/vs-dev11-expwin-long-md.md)], všechna upozornění mají úroveň závažnosti upozornění analýzy kódu.

##  <a name="BKMK_Warnings"></a> Upozornění analýzy kódu jazyka Visual Basic a C#
 Analýza kódu vyvolává následujícími upozorněními:

 [CA1001: Typy vlastních uvolnitelných polí, které by měly být uvolnitelné](http://msdn.microsoft.com/library/ms182172.aspx)

 [CA1821: Odstraňte prázdné finalizační metody](http://msdn.microsoft.com/library/bb264476.aspx)

 [CA2213: Uvolnitelné pole by mělo být uvolněno](http://msdn.microsoft.com/library/ms182328.aspx)

 [CA2229: Implementovat serializační konstruktory](http://msdn.microsoft.com/library/ms182343.aspx)

 [CA2231: Přetižte operátor equals při přepsání ValueType.Equals](http://msdn.microsoft.com/library/ms182359.aspx)
