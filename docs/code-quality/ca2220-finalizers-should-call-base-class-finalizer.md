---
title: 'CA2220: Finalizační metody by měly volat finalizační metodu základní třídy'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5af6b7872f0fa05183334e6acd2bc4922f84990
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231164"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Finalizační metody by měly volat finalizační metodu základní třídy

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Kategorie|Microsoft.Usage|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Typ, který Přepisuje <xref:System.Object.Finalize%2A?displayProperty=fullName> , <xref:System.Object.Finalize%2A> nevolá metodu v její základní třídě.

## <a name="rule-description"></a>Popis pravidla

Finalizační metoda musí být šířena přes hierarchii dědičnosti. Aby bylo zajištěno, typy musí volat svou metodu <xref:System.Object.Finalize%2A> základní třídy v rámci své <xref:System.Object.Finalize%2A> vlastní metody. C# Kompilátor automaticky přidá volání k finalizační metodě základní třídy.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, zavolejte <xref:System.Object.Finalize%2A> metodu základního typu z vaší <xref:System.Object.Finalize%2A> metody.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo. Některé kompilátory, které cílí na modul CLR (Common Language Runtime), vkládají volání finalizační metody základního typu do jazyka MSIL (Microsoft Intermediate Language). Pokud je oznámeno upozornění z tohoto pravidla, kompilátor nevloží volání a je nutné jej přidat do kódu.

## <a name="example"></a>Příklad

Následující příklad Visual Basic ukazuje typ `TypeB` , který správně <xref:System.Object.Finalize%2A> volá metodu v její základní třídě.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]

## <a name="see-also"></a>Viz také:

- [Vzor pro metodu Dispose](/dotnet/standard/design-guidelines/dispose-pattern)