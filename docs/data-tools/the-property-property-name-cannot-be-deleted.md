---
title: Vlastnost se nedá odstranit.
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 91fce94babf443c974a49885263b8e7eb77d9eaa
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281342"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>Vlastnost \<property name> nejde odstranit.

Vlastnost se \<property name> nedá odstranit, protože je nastavená jako **vlastnost diskriminátoru** pro dědičnost mezi \<class name> a.\<class name>

Vybraná vlastnost je nastavena jako **vlastnost diskriminátor** pro dědičnost mezi třídami uvedenými v chybové zprávě. Vlastnosti nelze odstranit, pokud se účastní konfigurace dědičnosti mezi datovými třídami.

Nastavte **vlastnost diskriminátor** na jinou vlastnost datové třídy, aby bylo možné povolit úspěšné odstranění požadované vlastnosti.

## <a name="to-correct-this-error"></a>Oprava této chyby

1. V **Návrháři o/R**vyberte čáru dědičnosti, která spojuje datové třídy uvedené v chybové zprávě.

2. Nastavte vlastnost **diskriminátor** na jinou vlastnost.

3. Zkuste vlastnost odstranit znovu.

## <a name="see-also"></a>Viz také

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)