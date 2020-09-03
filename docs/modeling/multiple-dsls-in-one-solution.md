---
title: Vícesouborové DSL v jediném řešení
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2eef29db24da3be0a9376ea76a9a1a551af9e1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542594"
---
# <a name="multiple-dsls-in-one-solution"></a>Vícesouborové DSL v jediném řešení

Můžete zabalit několik DSL jako součást jednoho řešení, aby byly nainstalovány dohromady.

K integraci více DSL můžete použít několik postupů. Další informace naleznete v tématu [integrování modelů pomocí sady Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) a [Postupy: Přidání obslužné rutiny přetahování myší](../modeling/how-to-add-a-drag-and-drop-handler.md) a [přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md).

## <a name="build-more-than-one-dsl-in-the-same-solution"></a>Sestavení více než jedné DSL ve stejném řešení

1. Vytvořte nový projekt **VSIX** projektu.

2. Vytvořte dva nebo více projektů DSL v adresáři řešení VSIX.

   - Pro každou DSL otevřete novou instanci sady Visual Studio. Vytvořte novou DSL a jako řešení VSIX zadejte stejnou složku řešení.

   - Nezapomeňte vytvořit každou DSL s jinou příponou názvu souboru.

   - Změňte názvy projektů **DSL** a **DslPackage** tak, aby se všechny lišily. Například: `Dsl1` , `DslPackage1` , `Dsl2` , `DslPackage2` .

   - V každém **DslPackage \* \ source.extension.TT**aktualizujte tento řádek na správný název projektu DSL:

      `string dslProjectName = "Dsl2";`

   - V rámci řešení VSIX přidejte projekty DSL * a DslPackage \* . Každou dvojici můžete umístit do vlastní složky řešení.

2. Kombinovat manifesty VSIX DSL:

   1. Otevřete _YourVsixProject_**\Source.extension.manifest**.

   2. U každé DSL vyberte **Přidat obsah** a přidejte:

       - `Dsl*` projekt jako **součást MEF**

       - `DslPackage*` projekt jako **součást MEF**

       - `DslPackage*` projekt jako **balíček vs**

3. Sestavte řešení.

   Výsledný VSIX bude instalovat obě DSL. Můžete je otestovat pomocí F5 nebo nasadit _YourVsixProject_**\bin\debug \\ \* . vsix**.

## <a name="see-also"></a>Viz také

- [Integrace modelů pomocí Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Postupy: Přidání obslužné rutiny operace přetažení myší](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md)