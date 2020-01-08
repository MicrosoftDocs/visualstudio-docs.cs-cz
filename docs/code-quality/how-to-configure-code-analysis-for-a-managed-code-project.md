---
title: Konfigurace analýzy kódu
ms.date: 04/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fe144e8de67264c9d89f6a240ef815afac9a4655
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587560"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Postupy: Konfigurace starší verze analýzy pro spravovaný kód

V sadě Visual Studio můžete zvolit ze seznamu [sad pravidel](../code-quality/rule-set-reference.md) analýzy kódu, které se mají použít pro projekt spravovaného kódu. Ve výchozím nastavení **Microsoft Minimální doporučená pravidla** je vybraná sada pravidel, můžete ale použít jinou sadu v případě potřeby pravidel. Sady pravidel lze použít na jeden nebo více projektů v řešení.

> [!NOTE]
> Tento článek se týká starší verze analýzy a [ne.NET Compiler Platform analyzátorů kódu na základě](use-roslyn-analyzers.md).

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>Konfigurace sady pravidel pro .NET Framework projekt

1. Otevřít **analýzy kódu** karty na stránkách vlastností projektu. Můžete to udělat některým z těchto způsobů:

   - V **Průzkumníka řešení**, vyberte projekt. Na panelu nabídek vyberte **analyzovat** > **konfigurovat analýzu kódu** > **pro \<projectname >** .

   - Klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** a vyberte **vlastnosti**a pak vyberte **analýzy kódu** kartu.

2. V **konfigurace** a **platformy** seznamy, vyberte sestavení konfigurace a cílovou platformu.

::: moniker range="vs-2017"

3. Chcete-li spustit analýzu kódu pokaždé, když je projekt sestaven pomocí vybrané konfigurace, vyberte možnost **Povolit analýzu kódu při sestavení**. Můžete také spustit analýzu kódu ručně tak, že vyberete **analyzovat** > **spustit analýzu kódu** > **spustit analýzu kódu na \<projectname >** .

::: moniker-end

::: moniker range=">=vs-2019"

3. Chcete-li spustit analýzu kódu pokaždé, když je projekt sestaven pomocí vybrané konfigurace, vyberte možnost **Spustit při sestavení** v části **binární analyzátory** . Můžete také spustit analýzu kódu ručně tak, že vyberete **analyzovat** > **spustit analýzu kódu** > **spustit analýzu kódu na \<projectname >** .

::: moniker-end

4. Chcete-li zobrazit upozornění z generovaného kódu, zrušte **potlačit Výsledky generovaného kódu** zaškrtávací políčko.

    > [!NOTE]
    > Tato možnost není potlačit chyby analýzy kódu a upozornění z generovaného kódu při chyby a upozornění se zobrazí ve formulářích a šablony. Zdrojový kód formuláře nebo šablony lze zobrazit a udržovat a nebude přepsán.

::: moniker range="vs-2017"

5. V **spustit tuto sadu pravidel** seznamu, proveďte jednu z následujících akcí:

::: moniker-end

::: moniker range=">=vs-2019"

5. V seznamu **aktivní pravidla** proveďte jednu z následujících akcí:

::: moniker-end

   - Vyberte sadu pravidel, který chcete použít.

   - Vyberte **\<procházet >** a vyhledejte existující sadu vlastních pravidel, která není v seznamu.

   - Definování [vlastní sady pravidel](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Určení sad pravidel pro více projektů v řešení

Ve výchozím nastavení, jsou přiřazeny všechny spravované projekty z řešení *Microsoft Minimální doporučená pravidla* sada pravidel analýzy kódu. Sady pravidel, které jsou přiřazeny k projektům v řešení můžete změnit **vlastnosti** dialogové okno pro řešení.

1. Otevřete řešení v sadě Visual Studio.

2. Na **analyzovat** nabídce vyberte možnost **konfigurovat analýzu kódu pro řešení**.

3. V případě potřeby rozbalit **společné vlastnosti**a pak vyberte **nastavení analýzy kódu**.

4. Můžete určit sadu pravidel pro jeden nebo více projektů:

    - Chcete-li určit sadu pravidel pro individuální projekt, vyberte název projektu.

    - Chcete-li určit sadu pravidel pro více projektů, podržte **Ctrl** a vyberte název projektu.

    - Chcete-li určit všechny projekty v řešení, podržte **Shift** a klikněte na tlačítko v seznamu projektu.

5. Vyberte **sady pravidel** pole projektu a pak vyberte název pravidla nastavit, že chcete použít.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace sady pravidel nástroje Analýza kódu](../code-quality/rule-set-reference.md)
