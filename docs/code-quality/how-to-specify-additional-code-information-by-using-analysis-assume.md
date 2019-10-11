---
title: Použití _Analysis_assume pro tipy pro analýzu kódu
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 186ea6ac58736098720d60c644c30801073b7453
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018728"
---
# <a name="how-to-specify-additional-code-information-by-using-_analysis_assume"></a>Postupy: Určení dalších informací o kódu pomocí funkce _Analysis_assume

Můžete poskytnout nápovědu nástroji pro analýzu kódu pro C/C++ kód, který pomůže procesu analýzy a omezit upozornění. Chcete-li zadat další informace, použijte následující funkci:

`_Analysis_assume(`  `expr`  `)`

`expr` – libovolný výraz, který se předpokládá, že se vyhodnotí jako true.

Nástroj Analýza kódu předpokládá, že podmínka reprezentovaná výrazem je pravdivá v místě, kde je funkce zobrazena a zůstává true, dokud není výraz změněn, například přiřazením proměnné.

> [!NOTE]
> `_Analysis_assume` nemá vliv na optimalizaci kódu. Mimo nástroj pro analýzu kódu je `_Analysis_assume` definováno jako No-op.

## <a name="example"></a>Příklad

Následující kód používá `_Analysis_assume` pro opravu upozornění analýzy kódu [C6388](../code-quality/c6388.md):

```cpp
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

// calls free and sets ch to null
void FreeAndNull(char** ch);

void test()
{
    char pc = (char)malloc(5);
    FreeAndNull(&pc);
    __analysis_assume(pc == NULL);
    f(pc);
}
```

## <a name="see-also"></a>Viz také:

- [__assume](/cpp/intrinsics/assume)
