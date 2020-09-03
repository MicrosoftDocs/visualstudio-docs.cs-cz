---
title: '&lt;Název vlastnosti vlastnosti &gt; nelze odstranit | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aca36919cb4c82d6ca76e0f3eecbbacd48cde768
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667245"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>&lt;Název vlastnosti vlastnosti &gt; nelze odstranit.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vlastnost se \<property name> nedá odstranit, protože je nastavená jako vlastnost diskriminátoru pro dědičnost mezi \<class name> a. \<class name>

 Vybraná vlastnost je nastavena jako **vlastnost diskriminátor** pro dědičnost mezi třídami uvedenými v chybové zprávě. Vlastnosti nelze odstranit, pokud se účastní konfigurace dědičnosti mezi datovými třídami.

 Nastavte **vlastnost diskriminátor** na jinou vlastnost datové třídy, aby bylo možné povolit úspěšné odstranění požadované vlastnosti.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. V Návrháři O/R vyberte čáru dědičnosti, která spojuje datové třídy uvedené v chybové zprávě.

2. Nastavte vlastnost **diskriminátor** na jinou vlastnost.

3. Zkuste vlastnost odstranit znovu.

## <a name="see-also"></a>Viz také
 [Postupy: Konfigurace dědičnosti s použitím](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) dědičnosti třídy dat návrháře o/r [(Návrhář o/r)](../data-tools/data-class-inheritance-o-r-designer.md) [: vytváření tříd LINQ to SQL pomocí dědičnosti s jednou tabulkou (o/r Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
