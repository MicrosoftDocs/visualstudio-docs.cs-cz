---
title: Vlastnost je uvedena dvakrát.
description: Nelze vytvořit vlastnost přidružení, která je uvedena dvakrát. Zobrazit informace o této zprávě aplikace Visual Studio Návrhář relací objektů (Návrhář O/R).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.technology: vs-data-tools
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d4cb795a5d608e31c26ccec0b96f359a5c63cee7
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2020
ms.locfileid: "94381776"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Nejde vytvořit &lt; název přidružení přidružení &gt; – vlastnost je uvedena dvakrát.

Nelze vytvořit přidružení \<association name> . Stejná vlastnost je uvedena více než jednou: \<property name> .

Přidružení jsou definována vybranými **vlastnostmi přidružení** v dialogovém okně **Editor přidružení** . Vlastnosti mohou být uvedeny pouze jednou pro každou třídu v asociaci.

Vlastnost ve zprávě se zobrazí více než jednou ve **vlastnostech přidružení** nadřazené nebo podřízené třídy.

## <a name="to-resolve-this-condition"></a>Vyřešení tohoto stavu

- Zkontrolujte zprávu a poznamenejte si vlastnost zadanou ve zprávě.

- Kliknutím na tlačítko **OK** zavřete okno se zprávou.

- Zkontrolujte **Vlastnosti přidružení** a odstraňte duplicitní položky.

- Klikněte na **OK**.

## <a name="see-also"></a>Viz také

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Postupy: vytvoření přidružení mezi třídami LINQ to SQL (Návrhář O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)