---
title: Vlastnost se nedá odstranit, protože se účastní přidružení.
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: aab2d2e3151786b45889262680d2f0815f684b6a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535379"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>&lt;Název vlastnosti vlastnosti &gt; nelze odstranit, protože se účastní &lt; názvu přidružení přidružení.&gt;

Vybraná vlastnost je nastavena jako **vlastnost Association** pro přidružení mezi třídami uvedenými v chybové zprávě. Vlastnosti nelze odstranit, pokud se účastní přidružení mezi třídami dat.

Nastavte **vlastnost Association** na jinou vlastnost datové třídy, aby bylo možné povolit úspěšné odstranění požadované vlastnosti.

## <a name="to-correct-this-error"></a>Oprava této chyby

1. Vyberte čáru přidružení v **Návrháři o/R** , který spojuje datové třídy, které jsou uvedeny v chybové zprávě.

2. Dvojitým kliknutím na řádek otevřete dialogové okno **Editor přidružení** .

3. Odeberte vlastnost z **vlastností přidružení**.

4. Zkuste vlastnost odstranit znovu.

## <a name="see-also"></a>Viz také:

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)