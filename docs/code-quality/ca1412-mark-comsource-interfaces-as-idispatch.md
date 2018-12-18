---
title: 'CA1412: Označte rozhraní ComSource jako IDispatch'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b992f546582fbd5b8bd82732b19ec4d72a6afd25
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549941"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: Označte rozhraní ComSource jako IDispatch

|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Kategorie|Microsoft.Interoperability|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina

Typ je označen pomocí <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> atribut a alespoň jednu zadanou rozhraní není označen atributem <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> atribut nastaven `InterfaceIsDispatch` hodnotu.

## <a name="rule-description"></a>Popis pravidla

<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> slouží k identifikaci událostí rozhraní, které třída poskytuje klientům modelu COM (Component Object). Tato rozhraní musí být vystavené jako `InterfaceIsIDispatch` povolení klientům modelu COM jazyka Visual Basic 6 příjem oznámení o události. Ve výchozím nastavení, pokud rozhraní není označen atributem <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> atribut, je vystavena jako duální rozhraní.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

Chcete-li opravit porušení tohoto pravidla, přidat nebo upravit <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> tak, aby jeho hodnota nastavená na InterfaceIsIDispatch pro všechna rozhraní, která jsou určena pomocí atributu <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> atribut.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad

Následující příklad ukazuje třídu, kde jednoho z rozhraní porušuje pravidlo.

[!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
[!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]

## <a name="related-rules"></a>Související pravidla

[CA1408: Nepoužívejte AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Viz také:

- [Spolupráce s nespravovaným kódem](/dotnet/framework/interop/index)