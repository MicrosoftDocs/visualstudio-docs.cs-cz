---
title: Vlastnost se nedá odstranit.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 29344a2443708d9ddaed3d90a186ab8424638664
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72640492"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>Vlastnost \<property název > nelze odstranit.

Vlastnost \<property název > nelze odstranit, protože je nastavena jako **vlastnost diskriminátor** pro dědičnost mezi \<class názvem > a \<classm názvem >

Vybraná vlastnost je nastavena jako **vlastnost diskriminátor** pro dědičnost mezi třídami uvedenými v chybové zprávě. Vlastnosti nelze odstranit, pokud se účastní konfigurace dědičnosti mezi datovými třídami.

Nastavte **vlastnost diskriminátor** na jinou vlastnost datové třídy, aby bylo možné povolit úspěšné odstranění požadované vlastnosti.

## <a name="to-correct-this-error"></a>Oprava této chyby

1. V **Návrháři o/R**vyberte čáru dědičnosti, která spojuje datové třídy uvedené v chybové zprávě.

2. Nastavte vlastnost **diskriminátor** na jinou vlastnost.

3. Zkuste vlastnost odstranit znovu.

## <a name="see-also"></a>Viz také:

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)