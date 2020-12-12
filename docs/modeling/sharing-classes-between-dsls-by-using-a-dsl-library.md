---
title: Sdílení tříd mezi DSL pomocí knihovny DSL
description: Přečtěte si, že v sadě Visual Studio vizualizace a modelování sady SDK můžete vytvořit nekompletní definici DSL, kterou můžete importovat do jiné DSL.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1685fe4fc7db6728ebc1ca6a12e27bb6f42589b
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363754"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Sdílení tříd mezi DSL pomocí knihovny DSL
V sadě Visual Studio vizualizace and modeling SDK můžete vytvořit nekompletní definici DSL, kterou můžete importovat do jiné DSL. To vám umožní zvážit společné části podobných modelů.

## <a name="creating-and-using-dsl-libraries"></a>Vytváření a používání knihoven DSL

#### <a name="to-create-a-dsl-library"></a>Vytvoření knihovny DSL

1. Vytvořte nový projekt DSL a vyberte šablonu řešení knihovny DSL.

     Jeden projekt DSL se vytvoří s prázdným modelem.

2. Můžete přidat doménové třídy, vztahy, obrazce atd.

     Elementy v knihovně nemusejí tvořit jeden strom pro vkládání.

     Chcete-li definovat vztah, který mohou používat importci, vytvořte dvě doménové třídy a mezi nimi vytvořte vztah.

     Zvažte nastavení **modifikátoru dědičnosti** doménových tříd na `Abstract` .

3. Můžete přidat prvky, které definujete v Průzkumníku DSL, jako jsou například tvůrci připojení.

4. Můžete přidat vlastní nastavení, která vyžadují další kód, například omezení ověřování.

5. Klikněte na **transformovat všechny šablony**.

6. Sestavte projekt.

7. Když distribuujete DSL pro jiné uživatele, musíte poskytnout zkompilované sestavení (DLL) i soubor `DslDefinition.dsl` . Zkompilované sestavení můžete najít ve složce pod `Dsl\bin\*`

#### <a name="to-import-a-dsl-library"></a>Import knihovny DSL

1. V jiné definici DSL v **Průzkumníkovi DSL** klikněte pravým tlačítkem na kořenovou třídu DSL a pak klikněte na **Přidat nový DslLibrary import**.

2. V okno Vlastnosti nastavte **cestu k souboru** knihovny. Můžete použít buď relativní, nebo absolutní cestu.

    Importovaná knihovna se zobrazí v Průzkumníku DSL v režimu jen pro čtení.

3. Můžete použít importované třídy jako základní třídy. Vytvořte doménovou třídu v importované DSL a v okno Vlastnosti nastavte **základní třídu** na importovanou třídu.

4. Klikněte na transformovat všechny šablony.

5. Přidejte do projektu DSL odkaz na sestavení (DLL), které bylo sestaveno projektem knihovny DSL.

6. Sestavte řešení.

   Knihovna DSL může importovat jiné knihovny. Při importu knihovny se její importy automaticky zobrazí také v Průzkumníku DSL.

## <a name="see-also"></a>Viz také:

- [Jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
