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
ms.openlocfilehash: 98db7cda02495d207d6e9387341173ea2efe22ca
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431349"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Postup: Konfigurace analýzy staršíverze pro spravovaný kód

V sadě Visual Studio můžete vybrat ze seznamu [sad pravidel](../code-quality/rule-set-reference.md) analýzy kódu, které se použijí pro projekt spravovaného kódu. Ve výchozím nastavení je vybrána sada pravidel **Minimální doporučená pravidla společnosti Microsoft,** ale v případě potřeby můžete použít jinou sadu pravidel. Sady pravidel lze použít na jeden nebo více projektů v řešení.

> [!NOTE]
> Tento článek se vztahuje na starší analýzy a nikoli na [analyzátory kódu založené na platformě .NET Compiler Platform](use-roslyn-analyzers.md).

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>Konfigurace sady pravidel pro projekt rozhraní .NET Framework

1. Otevřete kartu **Analýza kódu** na stránkách vlastností projektu. To lze provést jedním z následujících způsobů:

   - V **Průzkumníku řešení**vyberte projekt. Na řádku nabídek vyberte **Analyzovat** > **konfigurovat analýzu** > kódu**pro \<název projektu>**.

   - Klikněte pravým tlačítkem myši na projekt v **Průzkumníku řešení** a vyberte **Vlastnosti**a pak vyberte kartu **Analýza kódu.**

2. V seznamech **Konfigurace** a **Platforma** vyberte konfiguraci sestavení a cílovou platformu.

::: moniker range="vs-2017"

3. Chcete-li spustit analýzu kódu při každém sestavení projektu pomocí vybrané konfigurace, vyberte **možnost Povolit analýzu kódu při sestavení**. Analýzu kódu můžete spustit také ručně tak, že na>vyberete **analyzovat** > **analýzu** > spuštění analýzy kódu spuštění**analýzy \<kódu **.

::: moniker-end

::: moniker range=">=vs-2019"

3. Chcete-li spustit analýzu kódu při každém sestavení projektu pomocí vybrané konfigurace, vyberte **spustit při sestavení** v části Binární **analyzátory.** Analýzu staršíverze kódu můžete spustit také ručně, najdete v [tématu How to: Run Legacy Code Analysis Manually for Managed Code](how-to-run-legacy-code-analysis-manually-for-managed-code.md) for more details.

::: moniker-end

4. Chcete-li zobrazit upozornění z generovaného kódu, zrušte zaškrtnutí políčka **Potlačit výsledky z generovaného kódu.**

    > [!NOTE]
    > Tato možnost nepotlačí chyby analýzy kódu a upozornění z generovaného kódu, když se chyby a upozornění zobrazí ve formulářích a šablonách. Můžete zobrazit a udržovat zdrojový kód formuláře nebo šablony a nebude přepsán.

::: moniker range="vs-2017"

5. V seznamu **Spustit tuto sadu pravidel** proveďte jednu z následujících akcí:

::: moniker-end

::: moniker range=">=vs-2019"

5. V seznamu **Aktivní pravidla** proveďte jeden z následujících akcí:

::: moniker-end

   - Vyberte sadu pravidel, kterou chcete použít.

   - Vyberte ** \<Procházet>** a vyhledejte existující vlastní sadu pravidel, která není v seznamu.

   - Definujte [vlastní sadu pravidel](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Určení sad pravidel pro více projektů v řešení

Ve výchozím nastavení jsou všem spravovaným projektům řešení přiřazena sada pravidel analýzy kódu *minimálních doporučených pravidel společnosti Microsoft.* Sady pravidel, které jsou přiřazeny k projektům řešení, můžete změnit v dialogovém okně **Vlastnosti** řešení.

1. Otevřete řešení v sadě Visual Studio.

2. V nabídce **Analyzovat** vyberte **konfigurovat analýzu kódu pro řešení**.

3. V případě potřeby rozbalte **položku Společné vlastnosti**a pak vyberte **nastavení analýzy kódu**.

4. Můžete určit sadu pravidel pro jeden nebo více projektů:

    - Chcete-li určit sadu pravidel pro jednotlivé projekty, vyberte název projektu.

    - Chcete-li určit sadu pravidel pro více projektů, podržte **stisknutou klávesu Ctrl** a vyberte názvy projektů.

    - Chcete-li zadat všechny projekty v řešení, podržte **stisknutou klávesu Shift** a klepněte na seznam projektů.

5. Vyberte pole **Sada pravidel** projektu a pak vyberte název sady pravidel, kterou chcete použít.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace sady pravidel nástroje Analýza kódu](../code-quality/rule-set-reference.md)
