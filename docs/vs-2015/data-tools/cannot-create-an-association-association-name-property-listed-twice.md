---
title: Název přidružení přidružení nelze vytvořit &lt; &gt; – vlastnost je uvedena dvakrát | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9e4a1d20b5c341c1643836ae30e5de6243f35454
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662561"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Nejde vytvořit &lt; název přidružení přidružení &gt; – vlastnost je uvedena dvakrát.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nelze vytvořit přidružení \<association name> . Stejná vlastnost je uvedena více než jednou: \<property name> .

 Přidružení jsou definována vybranými **vlastnostmi přidružení** v dialogovém okně **Editor přidružení** . Vlastnosti mohou být uvedeny pouze jednou pro každou třídu v asociaci.

 Vlastnost ve zprávě se zobrazí více než jednou ve **vlastnostech přidružení**nadřazené nebo podřízené třídy.

### <a name="to-resolve-this-condition"></a>Vyřešení tohoto stavu

- Zkontrolujte zprávu a poznamenejte si vlastnost zadanou ve zprávě.

- Kliknutím na tlačítko **OK** zavřete okno se zprávou.

- Zkontrolujte **Vlastnosti přidružení** a odstraňte duplicitní položky.

- Klikněte na **OK**.

## <a name="see-also"></a>Viz také
 [LINQ to SQL nástroje v aplikaci Visual Studio](https://msdn.microsoft.com/library/a57e82d5-f7e4-4894-8add-3d9ba4fce186) [Postupy: vytvoření přidružení (relace) mezi LINQ to SQLmi třídami (o/r Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) [Návod: vytváření tříd LINQ to SQL (o-r Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
