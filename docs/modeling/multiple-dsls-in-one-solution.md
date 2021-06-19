---
title: Vícesouborové DSL v jediném řešení
description: Zjistěte, jak můžete zabalit několik jazyků specifických pro doménu (DSL) jako součást jednoho řešení, aby se nainstalovaly společně.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 11baf6439062e28c7361e2fabb4dea4a3430f237
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390916"
---
# <a name="multiple-dsls-in-one-solution"></a>Vícesouborové DSL v jediném řešení

Můžete zabalovat několik adres DSL jako součást jednoho řešení, aby se nainstalovaly společně.

K integraci více adres DSL můžete použít několik technik. Další informace najdete v tématu Integrace modelů pomocí [Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) a Postupy: Přidání obslužné rutiny [přetahováním a](../modeling/how-to-add-a-drag-and-drop-handler.md) [Přizpůsobení chování kopírování.](../modeling/customizing-copy-behavior.md)

## <a name="build-more-than-one-dsl-in-the-same-solution"></a>Sestavení více než jednoho DSL ve stejném řešení

1. Vytvořte nový projekt **projektu VSIX.**

2. Vytvořte dva nebo více projektů DSL v adresáři řešení VSIX.

   - Pro každý DSL otevřete novou instanci Visual Studio. Vytvořte nový DSL a zadejte stejnou složku řešení jako řešení VSIX.

   - Ujistěte se, že vytváříte každý DSL s jinou příponou názvu souboru.

   - Změňte názvy projektů **Dsl** a **DslPackage** tak, aby byly všechny odlišné. Například: `Dsl1` , `DslPackage1` , , `Dsl2` `DslPackage2` .

   - V každém **balíčku \* DslPackage \source.extension.tt** aktualizujte tento řádek na správný název projektu Dsl:

      `string dslProjectName = "Dsl2";`

   - V řešení VSIX přidejte projekty Dsl* a \* DslPackage. Každý pár můžete umístit do vlastní složky řešení.

2. Zkombinujte manifesty VSIX pro seznamy DSL:

   1. Otevřete _soubor YourVsixProject_**\source.extension.manifest**.

   2. Pro každý DSL zvolte **Přidat obsah a** přidejte:

       - `Dsl*` projekt jako **součást MEF**

       - `DslPackage*` projekt jako **součást MEF**

       - `DslPackage*` projekt jako **balíček VS**

3. Sestavte řešení.

   Výsledný soubor VSIX nainstaluje oba seznamy DSL. Můžete je otestovat pomocí klávesy F5 nebo nasadit _soubor YourVsixProject_**\bin\Debug \\ \* .vsix.**

## <a name="see-also"></a>Viz také

- [Integrace modelů pomocí Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Postupy: Přidání obslužné rutiny operace přetažení myší](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md)