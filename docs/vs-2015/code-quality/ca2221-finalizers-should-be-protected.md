---
title: 'CA2221: finalizační metody by měly být chráněné | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2221
- FinalizersShouldBeProtected
helpviewer_keywords:
- FinalizersShouldBeProtected
- CA2221
ms.assetid: bda03aee-4cce-45d3-907d-17f4ee030acc
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e30dd2945820a61aa7c96d4e6c6fd59354e0c3ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540735"
---
# <a name="ca2221-finalizers-should-be-protected"></a>CA2221: Finalizační metody by měly být chráněné
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|FinalizersShouldBeProtected|
|CheckId|CA2221|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Veřejný typ implementuje finalizační metodu, která neurčuje přístup Family (Protected).

## <a name="rule-description"></a>Popis pravidla
 Finalizační metody musí použít modifikátor přístupu family. Toto pravidlo je vynutilo kompilátory C#, Visual Basic a Visual C++.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte finalizační metodu tak, aby byla přístupná pro rodinu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Toto pravidlo se nedá porušovat v žádném jazyce .NET úrovně vyšší úrovně; může být porušena, pokud píšete Microsoft Intermediate Language.

```
// =============== CLASS MEMBERS DECLARATION ===================
//   note that class flags, 'extends' and 'implements' clauses
//          are provided here for information only

.namespace UsageLibrary
{
  .class public auto ansi beforefieldinit FinalizeMethodNotProtected
         extends [mscorlib]System.Object
  {
    .method public hidebysig instance void
            Finalize() cil managed
    {

      // Code size       1 (0x1)
      .maxstack  0
      IL_0000:  ret
    } // end of method FinalizeMethodNotProtected::Finalize

    .method public hidebysig specialname rtspecialname
            instance void  .ctor() cil managed
    {
      // Code size       7 (0x7)
      .maxstack  1
      IL_0000:  ldarg.0
      IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
      IL_0006:  ret
    } // end of method FinalizeMethodNotProtected::.ctor

  } // end of class FinalizeMethodNotProtected
} // end of namespace
```

## <a name="see-also"></a>Viz také
 [Vzor pro metodu Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
