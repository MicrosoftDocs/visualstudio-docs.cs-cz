---
title: 'CA1406: Vyhněte se argumentům Int64 pro klienty jazyka Visual Basic 6'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 82a8b1ea389c37dc63a9fe7366208a2a3028efb8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234797"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Vyhněte se argumentům Int64 pro klienty jazyka Visual Basic 6

|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|Kategorie|Microsoft. interoperabilita|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Typ, který je konkrétně označen jako viditelný pro model COM (Component Object Model), deklaruje člen, který přijímá <xref:System.Int64?displayProperty=fullName> argument.

## <a name="rule-description"></a>Popis pravidla
Klienty modulu COM jazyka Visual Basic 6 nemohou přistupovat k 64bitová celá čísla.

Ve výchozím nastavení jsou následující prvky viditelné v modelu COM: sestavení, veřejné typy, členy veřejné instance ve veřejných typech a všechny členy typů veřejné hodnoty. Chcete-li však omezit falešně pozitivní hodnoty, toto pravidlo vyžaduje explicitní zadání viditelnosti typu COM; obsahující <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> sestavení musí být označeno nastavením na `false` a typ <xref:System.Runtime.InteropServices.ComVisibleAttribute> musí být označen nastavením na `true`.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla pro parametr, jehož hodnota může být vždy vyjádřena jako 32 bitová integrál, změňte typ parametru na <xref:System.Int32?displayProperty=fullName>. Pokud hodnota parametru může být větší, než může být vyjádřena jako 32-bit integrál, změňte typ parametru na <xref:System.Decimal?displayProperty=fullName>. Všimněte si, <xref:System.Single?displayProperty=fullName> že <xref:System.Double?displayProperty=fullName> obě a ztrácejí přesnost v horních rozsahech <xref:System.Int64> datového typu. Pokud člen nemá být viditelný pro model COM, označte jej pomocí <xref:System.Runtime.InteropServices.ComVisibleAttribute> příkazu Set to. `false`

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Z tohoto pravidla je bezpečné potlačit upozornění, pokud je jisté, že Visual Basic 6 klientů modelu COM nebude přistupovat k tomuto typu.

## <a name="example"></a>Příklad
Následující příklad ukazuje typ, který je v rozporu s pravidlem.

[!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
[!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]

## <a name="related-rules"></a>Související pravidla
[CA1413: Vyhněte se neveřejným polím v viditelných hodnotových typech modelu COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

[CA1407: Vyhněte se statickým členům ve viditelných typech modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

[CA1017: Označte sestavení pomocí ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Viz také:

- [Spolupráce s nespravovaným kódem](/dotnet/framework/interop/index)
- [Datový typ Long](/dotnet/visual-basic/language-reference/data-types/long-data-type)