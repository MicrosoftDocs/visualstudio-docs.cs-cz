---
title: Konfigurace analýzy kódu
ms.date: 04/04/2018
description: Naučte se konfigurovat sadu pravidel, kterou používá nástroj analýza kódu starší verze sady Visual Studio. Podívejte se, jak použít sadu pravidel na jeden nebo více projektů v řešení.
ms.custom: SEO-VS-2020
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
- vs.codeanalysis.propertypages.asp
dev_langs:
- CSharp
- VB
- FSharp
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 8b76678b1e5c0f53502e24f8baee87ede3bd3ef6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860175"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Postupy: Konfigurace starší verze analýzy pro spravovaný kód

V sadě Visual Studio můžete zvolit ze seznamu [sad pravidel](../code-quality/rule-set-reference.md) analýzy kódu, které se mají použít pro projekt spravovaného kódu. Ve výchozím nastavení je vybraná sada pravidel **Minimální doporučená pravidla společnosti Microsoft** , ale v případě potřeby můžete použít jinou sadu pravidel. Sady pravidel lze použít pro jeden nebo více projektů v řešení.

> [!NOTE]
> Tento článek se týká starší verze analýzy a [ne.NET Compiler Platform analyzátorů kódu na základě](use-roslyn-analyzers.md).

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>Konfigurace sady pravidel pro .NET Framework projekt

1. Otevřete kartu **Analýza kódu** na stránkách vlastností projektu. Můžete to udělat jedním z těchto způsobů:

   - V **Průzkumník řešení** vyberte projekt. Na panelu nabídek vyberte **analyzovat**  >  **Konfigurovat analýzu kódu**  >  **pro \<projectname>**.

   - Klikněte pravým tlačítkem na projekt v **Průzkumník řešení** a vyberte **vlastnosti** a pak vyberte kartu **Analýza kódu** .

2. V seznamech **Konfigurace** a **platforma** vyberte konfigurace sestavení a cílová platforma.

::: moniker range="vs-2017"

3. Chcete-li spustit analýzu kódu pokaždé, když je projekt sestaven pomocí vybrané konfigurace, vyberte možnost **Povolit analýzu kódu při sestavení**. Analýzu kódu můžete spustit také ručně tak, že vyberete možnost **analyzovat**  >  **Spustit analýzu kódu**  >  **Spustit analýzu \<projectname> kódu na**.

::: moniker-end

::: moniker range=">=vs-2019"

3. Chcete-li spustit analýzu kódu pokaždé, když je projekt sestaven pomocí vybrané konfigurace, vyberte možnost **Spustit při sestavení** v části **binární analyzátory** . Můžete také spustit starší analýzu kódu ručně. Další informace naleznete v tématu [How to: Run Legacy Code Analysis for Managed Code](how-to-run-legacy-code-analysis-manually-for-managed-code.md) .

::: moniker-end

4. Chcete-li zobrazit upozornění z vygenerovaného kódu, zrušte zaškrtnutí políčka **Potlačit výsledky z vygenerovaného kódu** .

    > [!NOTE]
    > Tato možnost potlačí chyby a upozornění analýzy kódu z generovaného kódu, pokud se chyby a upozornění zobrazují ve formulářích a šablonách. Zdrojový kód formuláře nebo šablony lze zobrazit a udržovat a nebude přepsán.

::: moniker range="vs-2017"

5. V seznamu **Spustit tuto sadu pravidel** proveďte jednu z následujících akcí:

::: moniker-end

::: moniker range=">=vs-2019"

5. V seznamu **aktivní pravidla** proveďte jednu z následujících akcí:

::: moniker-end

   - Vyberte sadu pravidel, kterou chcete použít.

   - Tuto možnost vyberte **\<Browse>** , pokud chcete najít existující sadu vlastních pravidel, která není v seznamu.

   - Definujte [vlastní sadu pravidel](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Určení sad pravidel pro více projektů v řešení

Ve výchozím nastavení se všechny spravované projekty řešení přiřazují do sady pravidel *Microsoft minima pravidla* analýzy kódu. Můžete změnit sady pravidel, které jsou přiřazeny k projektům řešení v dialogovém okně **vlastnosti** pro dané řešení.

1. Otevřete řešení v sadě Visual Studio.

2. V nabídce **analyzovat** vyberte možnost **Konfigurovat analýzu kódu pro řešení**.

3. V případě potřeby rozbalte **společné vlastnosti** a pak vyberte **nastavení analýzy kódu**.

4. Pro jeden nebo více projektů můžete zadat sadu pravidel:

    - Chcete-li zadat sadu pravidel pro jednotlivé projekty, zvolte název projektu.

    - Chcete-li zadat sadu pravidel pro více projektů, vyberte možnost **CTRL** a názvy projektů.

    - Chcete-li zadat všechny projekty v řešení, vyberte možnost **SHIFT** a seznam projektu.

5. Vyberte pole **sada pravidel** projektu a potom vyberte název sady pravidel, kterou chcete použít.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace sady pravidel nástroje Analýza kódu](../code-quality/rule-set-reference.md)
