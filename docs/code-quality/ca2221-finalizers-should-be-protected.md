---
title: 'CA2221: Finalizační metody by měly být chráněné'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2221
- FinalizersShouldBeProtected
helpviewer_keywords:
- FinalizersShouldBeProtected
- CA2221
ms.assetid: bda03aee-4cce-45d3-907d-17f4ee030acc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1ac3f9116366920f833fe8d907181473d6fda106
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551282"
---
# <a name="ca2221-finalizers-should-be-protected"></a>CA2221: Finalizační metody by měly být chráněné

|||
|-|-|
|TypeName|FinalizersShouldBeProtected|
|CheckId|CA2221|
|Kategorie|Microsoft.Usage|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina
 Veřejný typ implementuje finalizační metodu, která neurčuje přístupu family (chráněné).

## <a name="rule-description"></a>Popis pravidla
 Finalizační metody musí použít modifikátor přístupu family. Toto pravidlo je vynuceno kompilátory C#, Visual Basic a Visual C++.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte finalizační metodu dostupná řada.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Toto pravidlo nemůže být došlo k porušení v kterémkoli jazyce platformy .NET vysoké úrovně; Pokud píšete jazyk Microsoft Intermediate Language protože porušoval.

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

## <a name="see-also"></a>Viz také:

- [Vzor pro metodu Dispose](/dotnet/standard/design-guidelines/dispose-pattern)