---
title: Vlastnost &lt;property název &gt; nelze odstranit, protože se účastní názvu &lt;association přidružení &gt; | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 53bf12a84a705ddca0cacffc36028698cb08443a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667276"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Vlastnost &lt;property název &gt; nelze odstranit, protože se účastní názvu &lt;association přidružení &gt;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vybraná vlastnost je nastavena jako **vlastnost Association** pro přidružení mezi třídami uvedenými v chybové zprávě. Vlastnosti nelze odstranit, pokud se účastní přidružení mezi třídami dat.

 Nastavte **vlastnost Association** na jinou vlastnost datové třídy, aby bylo možné povolit úspěšné odstranění požadované vlastnosti.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Vyberte čáru přidružení v Návrháři O/R, který spojuje datové třídy, které jsou uvedeny v chybové zprávě.

2. Dvojitým kliknutím na řádek otevřete dialogové okno **Editor přidružení** .

3. Odeberte vlastnost z **vlastností přidružení**.

4. Zkuste vlastnost odstranit znovu.

## <a name="see-also"></a>Viz také
 [LINQ to SQL nástroje v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [Postupy: vytvoření přidružení (relace) mezi LINQ to SQLmi třídami (o/r Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) [Návod: vytváření tříd LINQ to SQL (o-r Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
