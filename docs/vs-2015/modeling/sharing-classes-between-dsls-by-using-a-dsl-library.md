---
title: Sdílení tříd mezi DSL pomocí knihovny DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 509bd96b-3e66-47f4-8642-771421d0d0d5
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 093cc277fa1cbe1915099fd9663fc1ccb797ca3a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671184"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Sdílení tříd mezi DSL pomocí knihovny DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sadě vizualizace a modelování sady SDK můžete vytvořit nekompletní definici DSL, kterou můžete importovat do jiné DSL. To vám umožní zvážit společné části podobných modelů.

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

1. V jiné definici DSL v **Průzkumníkovi DSL**klikněte pravým tlačítkem na kořenovou třídu DSL a pak klikněte na **Přidat nový DslLibrary import**.

2. V okno Vlastnosti nastavte **cestu k souboru** knihovny. Můžete použít buď relativní, nebo absolutní cestu.

    Importovaná knihovna se zobrazí v Průzkumníku DSL v režimu jen pro čtení.

3. Můžete použít importované třídy jako základní třídy. Vytvořte doménovou třídu v importované DSL a v okno Vlastnosti nastavte **základní třídu** na importovanou třídu.

4. Klikněte na transformovat všechny šablony.

5. Přidejte do projektu DSL odkaz na sestavení (DLL), které bylo sestaveno projektem knihovny DSL.

6. Sestavte řešení.

   Knihovna DSL může importovat jiné knihovny. Při importu knihovny se její importy automaticky zobrazí také v Průzkumníku DSL.

## <a name="see-also"></a>Viz také
 [Jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md)
