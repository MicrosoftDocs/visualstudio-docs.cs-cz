---
title: 'Postupy: určení dalších informací o kódu pomocí __analysis_assume | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- __analysis_assume
helpviewer_keywords:
- __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: f2f18c9284ec96de7a7b8663aff485962d194282
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277972"
---
# <a name="how-to-specify-additional-code-information-by-using-__analysis_assume"></a>Postupy: Určení dalších informací o kódu pomocí __analysis_assume
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete poskytnout nápovědu nástroji pro analýzu kódu pro C/C++ kód, který pomůže procesu analýzy a omezit upozornění. Chcete-li zadat další informace, použijte následující funkci:  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr` – libovolný výraz, který se předpokládá pro vyhodnocení na hodnotu true.  
  
 Nástroj Analýza kódu předpokládá, že podmínka reprezentovaná výrazem je pravdivá v místě, kde je funkce zobrazena a zůstává true, dokud není výraz změněn, například přiřazením proměnné.  
  
> [!NOTE]
> `__analysis_assume` nemá vliv na optimalizaci kódu. Mimo nástroj pro analýzu kódu je `__analysis_assume` definováno jako No-op.  
  
## <a name="example"></a>Příklad  
 Následující kód používá `__analysis_assume` k opravě upozornění analýzy kódu [C6388](../code-quality/c6388.md):  
  
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
  __analysis_assume(pc == NULL);   
  f(pc);  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [__assume](https://msdn.microsoft.com/library/d8565123-b132-44b1-8235-5a8c8bff85a7)
