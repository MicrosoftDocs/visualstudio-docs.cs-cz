---
title: 'CA1412: Označte rozhraní ComSource jako IDispatch'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: caaae787d5e4801f3fc3b8d881b386595fb2eca4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234680"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: Označte rozhraní ComSource jako IDispatch

|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Kategorie|Microsoft. interoperabilita|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Typ je označen <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> atributem a alespoň jedno zadané rozhraní není označeno <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> atributem nastaveným na `InterfaceIsDispatch` hodnotu.

## <a name="rule-description"></a>Popis pravidla

<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>slouží k identifikaci rozhraní události, které třída zveřejňuje klientům modelu COM (Component Object Model). Tato rozhraní musí být vystavena `InterfaceIsIDispatch` , aby umožnila Visual Basic 6 klientů modelu COM, aby přijímala oznámení o událostech. Ve výchozím nastavení, pokud rozhraní není označeno <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> atributem, je vystaveno jako duální rozhraní.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, přidejte nebo upravte <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> atribut tak, aby byla jeho hodnota nastavena na InterfaceIsIDispatch pro všechna rozhraní, která jsou zadána <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> s atributem.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad

Následující příklad ukazuje třídu, kde jedno z rozhraní je v rozporu s pravidlem.

[!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
[!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]

## <a name="related-rules"></a>Související pravidla

[CA1408: Nepoužívat AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Viz také:

- [Spolupráce s nespravovaným kódem](/dotnet/framework/interop/index)