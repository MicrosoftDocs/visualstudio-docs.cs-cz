---
title: 'CA1810: Inicializujte odkazový typ statického pole vloženě'
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5e6f65c8b8c570f8df142c36f85388b68b66d3b0
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233659"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810: Inicializujte odkazový typ statického pole vloženě

|||
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|CheckId|CA1810|
|Kategorie|Microsoft. Performance|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Typ odkazu deklaruje explicitní statický konstruktor.

## <a name="rule-description"></a>Popis pravidla
Pokud typ deklaruje explicitní statický konstruktor, kompilátor just-in-time (JIT) ke každé statické metodě a konstruktoru instance tohoto typu přidá kontrolu, zda již byl dříve statický konstruktor zavolán. Statická inicializace se aktivuje, když se přistupuje ke statickému členu nebo když je vytvořená instance typu. Statická inicializace však není aktivována, pokud deklarujete proměnnou typu, ale nepoužijete ji, což může být důležité, pokud se změní globální stav inicializace.

Když jsou všechna statická data inicializována vložená a explicitní statický konstruktor není deklarován, kompilátory jazyka MSIL (Microsoft Intermediate Language) přidají `beforefieldinit` příznak a implicitní statický konstruktor, který inicializuje statická data, na typ MSIL definition. Když kompilátor JIT narazí na `beforefieldinit` příznak, většinou se nepřidá kontrola statického konstruktoru. Statická inicializace je zaručena v určitou dobu před tím, než dojde ke statickým polím, ale ne před vyvoláním statické metody nebo konstruktoru instance. Všimněte si, že statická inicializace může nastat kdykoli po deklarování proměnné typu.

Kontroly statického konstruktoru mohou snížit výkon. Statický konstruktor se často používá pouze k inicializaci statických polí. v takovém případě je nutné zajistit, aby před prvním přístupem ke statickému poli došlo ke statické inicializaci. `beforefieldinit` Chování je vhodné pro tyto a většinu ostatních typů. Je nevhodný pouze v případě, že statická inicializace má vliv na globální stav a jedna z následujících hodnot je true:

- Vliv na globální stav je nákladný a není povinný, pokud se typ nepoužívá.

- K globálním dopadům na stav lze získat přístup bez přístupu ke statickým polím typu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, inicializujte všechna statická data při deklaraci a statický konstruktor odeberte.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Z tohoto pravidla je bezpečné potlačit upozornění, pokud výkon není obavou; nebo v případě, že změny globálních stavů, které jsou způsobeny statickou inicializací jsou nákladné nebo musí být zaručeny, aby vznikly před voláním statické metody typu nebo je vytvořena instance typu.

## <a name="example"></a>Příklad

Následující příklad ukazuje typ, `StaticConstructor`, který porušuje pravidlo a typ, `NoStaticConstructor`, který nahrazuje statický konstruktor s vloženou inicializací pro splnění pravidla.

[!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/CSharp/ca1810-initialize-reference-type-static-fields-inline_1.cs)]
[!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/VisualBasic/ca1810-initialize-reference-type-static-fields-inline_1.vb)]

Všimněte si přidání `beforefieldinit` příznaku do definice MSIL `NoStaticConstructor` pro třídu.

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

- [CA2207: Inicializovat vloženou hodnotu statických polí](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)