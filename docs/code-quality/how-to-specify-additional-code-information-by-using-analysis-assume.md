---
title: 'Postupy: určení informací další kód pomocí _Analysis_assume'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: ce8102bbc790019490c4dc2a2ccbfab7d8c33981
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
ms.locfileid: "32031524"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Postupy: určení informací další kód pomocí _Analysis_assume
Můžete zadat pomocné parametry nástroj pro analýzu kódu pro C/C++ kód, který bude pomůže procesu analýzy a snížit upozornění. Pokud chcete zadat další informace, použijte následující funkce:

 `_Analysis_assume(`  `expr`  `)`

 `expr` -libovolný výraz, který se předpokládá, že vyhodnotit na hodnotu true.

 Nástroj pro analýzu kódu předpokládá, že je hodnota true, v okamžiku, kdy funkce se zobrazí a zůstane hodnotu true, dokud je změnit výraz, například v podle přiřazení do proměnné, podmínky reprezentována výrazem.

> [!NOTE]
>  `_Analysis_assume` Optimalizace kódu neovlivní. Mimo nástroj pro analýzu kódu `_Analysis_assume` je definován jako no-op.

## <a name="example"></a>Příklad
 Následující kód používá `_Analysis_assume` opravit upozornění analýzy kódu [C6388](../code-quality/c6388.md):

```
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

// calls free and sets ch to null
void FreeAndNull(char* ch);

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

void test( )
{
  char *pc = (char*)malloc(5);
  FreeAndNull(pc);
  _Analysis_assume(pc == NULL);
  f(pc);
}
```

## <a name="see-also"></a>Viz také
 [__assume](/cpp/intrinsics/assume)