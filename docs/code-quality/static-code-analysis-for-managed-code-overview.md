---
title: Starší verze analýzy pro spravovaný kód
ms.date: 06/12/2019
description: Přečtěte si o starších verzích analýz v aplikaci Visual Studio. Podívejte se, jak potlačit upozornění a jak spouštět analýzy ručně, automaticky a při vrácení se změnami a sestavením.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: e8d9ddf88086772e0cd21bde856184954bc7143b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867682"
---
# <a name="overview-of-legacy-analysis-for-managed-code-in-visual-studio"></a>Přehled starší verze analýzy pro spravovaný kód v aplikaci Visual Studio

Visual Studio může analyzovat kód spravovaného kódu dvěma způsoby: pomocí [starší verze analýzy](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), označované také jako FxCop statická analýza spravovaných sestavení a s pokročilejšími [analyzátory kódu](../code-quality/roslyn-analyzers-overview.md)založeného na .NET Compiler Platform. Toto téma se zabývá analýzou starší verze. Další informace o analýze kódu na základě .NET Compiler Platform najdete v tématu [Přehled analyzátorů založených na .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md).

Analýza kódu pro spravovaný kód analyzuje spravovaná sestavení a sestavuje informace o sestaveních, jako jsou porušení pravidel programování a návrhu stanovených v [pokynech pro návrh .NET](/dotnet/standard/design-guidelines/).

Nástroj pro analýzu představuje kontroly, které provádí během analýzy, jako varovné zprávy. Varovné zprávy identifikují relevantní problémy s programováním a návrhem a, pokud je to možné, poskytují informace o tom, jak tento problém vyřešit.

> [!NOTE]
> Pro projekty .NET Core a .NET Standard v aplikaci Visual Studio není podporována starší verze analýzy (Analýza statického kódu). Pokud jako součást MSBuild spustíte analýzu kódu v projektu .NET Core nebo .NET Standard, zobrazí se chyba podobná **chybě: CA0055: nelze identifikovat platformu pro \<your.dll>**. Chcete-li analyzovat kód v projektech .NET Core nebo .NET Standard, použijte místo toho [analyzátory kódu](../code-quality/roslyn-analyzers-overview.md) .

## <a name="ide-integrated-development-environment-integration"></a>Integrace integrovaného vývojového prostředí (IDE)

Můžete spustit analýzu kódu v projektu ručně nebo automaticky.

Chcete-li spustit analýzu kódu pokaždé, když sestavíte projekt, vyberte možnost na stránce vlastností **Analýza kódu** projektu. Další informace najdete v tématu [Postup: povolení a zákaz automatické analýzy kódu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Chcete-li spustit analýzu kódu ručně v projektu, z panelu nabídek vyberte možnost **analyzovat**  >  **spuštění analýza kódu**  >  **Spustit analýzu kódu \<project> na**.

## <a name="rule-sets"></a>Sady pravidel

Pravidla analýzy kódu pro spravovaný kód jsou seskupena do [sad pravidel](../code-quality/using-rule-sets-to-group-code-analysis-rules.md). Můžete použít jednu ze standardních sad pravidel společnosti Microsoft, nebo můžete [vytvořit vlastní sadu pravidel](../code-quality/how-to-create-a-custom-rule-set.md) , která bude splňovat konkrétní potřebnou potřebu.

## <a name="suppress-warnings"></a>Potlačení upozornění

Často je užitečné indikovat, že upozornění není k dispozici. Tím se vývojář informuje a další lidé, kteří si mohou kód později projít, že bylo prověřeno upozornění a pak potlačí nebo ignoruje.

Potlačení upozornění v rámci zdroje je implementováno prostřednictvím vlastních atributů. Chcete-li potlačit upozornění, přidejte atribut `SuppressMessage` do zdrojového kódu, jak je znázorněno v následujícím příkladu:

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Další informace najdete v tématu [potlačení upozornění](../code-quality/in-source-suppression-overview.md).

::: moniker range="vs-2017"

> [!NOTE]
> Pokud migrujete projekt do sady Visual Studio 2017, může dojít k náhlému vynechání velkého počtu upozornění analýzy kódu. Pokud nejste připraveni na opravu upozornění, můžete je potlačit kliknutím na možnost **analyzovat**  >  **spuštění analýza kódu a potlačit aktivní problémy**.
>
> ![Spustit analýzu kódu a potlačit problémy v aplikaci Visual Studio](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Pokud migrujete projekt do sady Visual Studio 2019, může dojít k náhlému vynechání velkého počtu upozornění analýzy kódu. Pokud nejste připraveni opravit upozornění, můžete je potlačit výběrem možnosti **analyzovat**  >  **sestavení a potlačit aktivní problémy**.

::: moniker-end

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Spustit analýzu kódu jako součást zásady vracení se změnami

Jako organizace budete možná chtít vyžadovat, aby všechna vrácení se změnami splňovala určité zásady. Zejména se chcete ujistit, že dodržujete tyto zásady:

- V kódu nejsou registrovány žádné chyby sestavení.

- Analýza kódu se spouští jako součást nejnovějšího buildu.

To můžete provést zadáním zásad vracení se změnami. Další informace najdete v tématu [zvýšení kvality kódu pomocí zásad vracení zpět se změnami projektu](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md).

## <a name="team-build-integration"></a>Integrace sestavení týmu

Můžete použít integrované funkce systému sestavení ke spuštění nástroje pro analýzu jako součást procesu sestavení. Další informace najdete v tématu [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

## <a name="see-also"></a>Viz také

- [Přehled analyzátorů založených na .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md)
- [Použití sad pravidel k seskupování pravidel analýzy kódu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Postupy: Povolení a zákaz automatické analýzy kódu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
