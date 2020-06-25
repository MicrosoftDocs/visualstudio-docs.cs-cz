---
title: Nelze vytvořit vlastnost přidružení, která je uvedena dvakrát.
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 92999e211ec0f7265f026446e09dbc94cc3060f3
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282797"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Nejde vytvořit &lt; název přidružení přidružení &gt; – vlastnost je uvedena dvakrát.

Nelze vytvořit přidružení \<association name> . Stejná vlastnost je uvedena více než jednou: \<property name> .

Přidružení jsou definována vybranými **vlastnostmi přidružení** v dialogovém okně **Editor přidružení** . Vlastnosti mohou být uvedeny pouze jednou pro každou třídu v asociaci.

Vlastnost ve zprávě se zobrazí více než jednou ve **vlastnostech přidružení**nadřazené nebo podřízené třídy.

## <a name="to-resolve-this-condition"></a>Vyřešení tohoto stavu

- Zkontrolujte zprávu a poznamenejte si vlastnost zadanou ve zprávě.

- Kliknutím na tlačítko **OK** zavřete okno se zprávou.

- Zkontrolujte **Vlastnosti přidružení** a odstraňte duplicitní položky.

- Klikněte na **OK**.

## <a name="see-also"></a>Viz také

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Postupy: vytvoření přidružení mezi třídami LINQ to SQL (Návrhář O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)