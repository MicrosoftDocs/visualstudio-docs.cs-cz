---
title: Použití poznámek SAL k snížení míry výskytu závad kódu C/C++
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- annotations
- SAL annotations
- code analysis, annotation
ms.assetid: a16e47d0-6f3e-4ed6-8883-459b2874e9a4
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 506e8516c7a7bbc0ccc610b843763017ae90f547
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2019
ms.locfileid: "72807058"
---
# <a name="using-sal-annotations-to-reduce-cc-code-defects"></a>Použití poznámek SAL k snížení míry výskytu závad kódu C/C++
SAL je jazyk poznámky ke zdrojovému kódu společnosti Microsoft. Pomocí poznámek zdrojového kódu můžete provést explicitní záměr za kódem. Tyto poznámky také umožňují automatizované statické analytické nástroje k přesnější analýze kódu, s podstatně menším počtem falešně pozitivních a falešně negativních hodnot.

Články v této části dokumentace projednávají aspekty SAL, poskytují referenční informace pro syntaxi SAL a poskytují příklady jejich použití.

- [Porozumění SAL](../code-quality/understanding-sal.md)

     Obsahuje informace a příklady, které ukazují základní poznámky SAL.

- [Zadávání poznámek k parametrům funkcí a návratovým hodnotám](../code-quality/annotating-function-parameters-and-return-values.md)

     Obsahuje poznámky SAL pro funkce a parametry funkce.

- [Zadávání poznámek k chování funkcí](../code-quality/annotating-function-behavior.md)

     Obsahuje poznámky SAL pro chování funkcí a funkcí.

- [Zadávání poznámek ke strukturám a třídám](../code-quality/annotating-structs-and-classes.md)

     Zobrazuje poznámky SAL pro struktury a třídy.

- [Zadávání poznámek o chování při zamykání](../code-quality/annotating-locking-behavior.md)

     Vysvětluje, jak používat poznámky SAL s mechanismy zámku.

- [Určení, kdy a kde se má poznámka použít](../code-quality/specifying-when-and-where-an-annotation-applies.md)

     Obsahuje poznámky SAL, které určují podmínku nebo rozsah (umístění) jiných poznámek SAL.

- [Vnitřní funkce](../code-quality/intrinsic-functions.md)

     Zobrazí seznam vnitřních poznámek SAL.

- [Doporučené postupy a příklady](../code-quality/best-practices-and-examples-sal.md)

     Obsahuje příklady, které ukazují, jak používat poznámky SAL. Vysvětluje také běžné nástrah.

## <a name="related-resources"></a>Související prostředky
[Blog týmu analýzy kódu](https://blogs.msdn.microsoft.com/codeanalysis/)

## <a name="see-also"></a>Viz také
[Poznámky SAL 2,0 pro ovladače Windows](/windows-hardware/drivers/devtest/sal-2-annotations-for-windows-drivers)
