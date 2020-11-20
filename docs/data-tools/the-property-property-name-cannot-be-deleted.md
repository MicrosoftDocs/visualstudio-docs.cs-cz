---
title: Vlastnost se nedá odstranit.
description: Vlastnost nelze odstranit. Zobrazit informace o této zprávě aplikace Visual Studio Návrhář relací objektů (Návrhář O/R).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: bdca9758116c551604b5f75f141c15107c1fc890
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998357"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>Vlastnost \<property name> nejde odstranit.

Vlastnost se \<property name> nedá odstranit, protože je nastavená jako **vlastnost diskriminátoru** pro dědičnost mezi \<class name> a. \<class name>

Vybraná vlastnost je nastavena jako **vlastnost diskriminátor** pro dědičnost mezi třídami uvedenými v chybové zprávě. Vlastnosti nelze odstranit, pokud se účastní konfigurace dědičnosti mezi datovými třídami.

Nastavte **vlastnost diskriminátor** na jinou vlastnost datové třídy, aby bylo možné povolit úspěšné odstranění požadované vlastnosti.

## <a name="to-correct-this-error"></a>Oprava této chyby

1. V **Návrháři o/R** vyberte čáru dědičnosti, která spojuje datové třídy uvedené v chybové zprávě.

2. Nastavte vlastnost **diskriminátor** na jinou vlastnost.

3. Zkuste vlastnost odstranit znovu.

## <a name="see-also"></a>Viz také

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)