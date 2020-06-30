---
title: Nelze vytvořit vlastnost přidružení, která je uvedena dvakrát.
ms.date: 11/04/2016
ms.topic: error-reference
ms.technology: vs-data-tools
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 50c9311ef09172ea082d2419495f26b51ff1d6a4
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85536796"
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