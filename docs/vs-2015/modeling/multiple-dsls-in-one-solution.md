---
title: Více DSL v jednom řešení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9a3b35e05108db879b365b9cafc39cacdf843397
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668556"
---
# <a name="multiple-dsls-in-one-solution"></a>Vícesouborové DSL v jediném řešení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete zabalit několik DSL jako součást jednoho řešení, aby byly nainstalovány dohromady.

 K integraci více DSL můžete použít několik postupů. Další informace naleznete v tématu [integrování modelů pomocí sady Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) a [Postupy: Přidání obslužné rutiny přetahování myší](../modeling/how-to-add-a-drag-and-drop-handler.md) a [přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md).

### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>Sestavení více než jedné DSL ve stejném řešení

1. Vytvořte dvě nebo více řešení DSL a projekt VSIX a přidejte všechny projekty do jediného řešení.

   - Chcete-li vytvořit nový projekt VSIX: v dialogovém okně **Nový projekt** vyberte **možnost C#Visual** , **rozšiřitelnost**, **projekt VSIX**.

   - V adresáři řešení VSIX vytvořte dvě nebo více řešení DSL.

        Pro každou DSL otevřete novou instanci sady Visual Studio. Vytvořte novou DSL a jako řešení VSIX zadejte stejnou složku řešení.

        Nezapomeňte vytvořit každou DSL s jinou příponou názvu souboru.

   - Změňte názvy projektů **DSL** a **DslPackage** tak, aby se všechny lišily. Například: `Dsl1`, `DslPackage1`, `Dsl2` `DslPackage2`.

   - V každém **DslPackage \* \ source.extension.TT**aktualizujte tento řádek na správný název projektu DSL:

        `string dslProjectName = "Dsl2";`

   - V rámci řešení VSIX přidejte \* projekty DSL * a DslPackage.

        Každou dvojici můžete umístit do vlastní složky řešení.

2. Kombinovat manifesty VSIX DSL:

   1. Otevřete _YourVsixProject_ **\Source.extension.manifest**.

   2. U každé DSL vyberte **Přidat obsah** a přidejte:

       - `Dsl*` projekt jako **součást MEF**

       - `DslPackage*` projekt jako **součást MEF**

       - `DslPackage*` projekt jako **balíček vs**

3. Sestavte řešení.

   Výsledný VSIX bude instalovat obě DSL. Můžete je otestovat pomocí F5 nebo nasadit _YourVsixProject_ **\bin\debug \\ \*. vsix**.

## <a name="see-also"></a>Viz také
 [Integrace modelů pomocí sady Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) [Postupy: Přidání obslužné rutiny přetažení myší](../modeling/how-to-add-a-drag-and-drop-handler.md) [přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md)
