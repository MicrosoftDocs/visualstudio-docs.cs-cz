---
title: 'CA1810: Inicializujte odkazový typ statického pole vloženě'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2a6fdfebe506fb2edb1814e18d3d090025c665fa
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549440"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810: Inicializujte odkazový typ statického pole vloženě

|||
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|CheckId|CA1810|
|Kategorie|Microsoft.Performance|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Odkaz na typ deklaruje explicitní statický konstruktor.

## <a name="rule-description"></a>Popis pravidla
 Pokud typ deklaruje explicitní statický konstruktor, kompilátor just-in-time (JIT) ke každé statické metodě a konstruktoru instance tohoto typu přidá kontrolu, zda již byl dříve statický konstruktor zavolán. Statická inicializace se aktivuje při přístupu k jakékoli statického člena, nebo když je vytvořena instance typu. Statická inicializace ale neaktivuje, pokud deklarujete proměnnou typu, ale nepoužívejte ho, což může být důležité v případě, že inicializace mění globální stav.

 Všechna statická data je inicializována vložené a explicitní statický konstruktor není deklarován, kompilátory Microsoft intermediate language (MSIL) přidá `beforefieldinit` příznak a implicitní statický konstruktor, který inicializuje statických dat na typ jazyka MSIL definice. Když kompilátor JIT narazí `beforefieldinit` příznak, ve většině případů se nepřidají kontroly statického konstruktoru. Statická inicializace je zaručeno, ke kterým dochází za nějakou dobu předtím, než jsou přístupné žádná statická pole, ale ne předtím, než se vyvolá statickou metodu nebo instanci konstruktoru. Všimněte si, že se, že statická inicializace může probíhat kdykoli po deklarovat proměnnou typu.

 Kontroly statického konstruktoru mohou snížit výkon. Statický konstruktor se často slouží jenom k inicializaci statická pole, ve kterých je jenom nutné, že statická inicializace v tomto případě před první přístup statické pole. `beforefieldinit` Chování je vhodné pro tyto a většinu ostatních typů. Je jenom nevhodný při Statická inicializace má vliv na globální stav a je splněna jedna z následujících akcí:

- Vliv na globální stav je nákladné a není potřeba, pokud typ není použit.

- Globální stav účinky lze přistupovat bez přístupu k jakékoli statická pole typu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, inicializujte všechna statická data při deklaraci a statický konstruktor odeberte.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění tohoto pravidla, pokud výkon není žádný problém; nebo pokud globální stav změny, které jsou způsobeny Statická inicializace je vždycky musí zaručit udělat předtím, než je volána statická metoda typu nebo je vytvořena instance typu.

## <a name="example"></a>Příklad

Následující příklad ukazuje typ, `StaticConstructor`, který porušuje pravidla a typ, `NoStaticConstructor`, vložené inicializace splňovat pravidla, která nahradí statický konstruktor.

[!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/CSharp/ca1810-initialize-reference-type-static-fields-inline_1.cs)]
[!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/VisualBasic/ca1810-initialize-reference-type-static-fields-inline_1.vb)]

Poznámka: přidání `beforefieldinit` příznak na definici jazyka MSIL `NoStaticConstructor` třídy.

```
.class public auto ansi StaticConstructor
extends [mscorlib]System.Object
{
} // end of class StaticConstructor

.class public auto ansi beforefieldinit NoStaticConstructor
extends [mscorlib]System.Object
{
} // end of class NoStaticConstructor
```

## <a name="related-rules"></a>Související pravidla

- [CA2207: Inicializujte vloženou hodnotu statických polí](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)