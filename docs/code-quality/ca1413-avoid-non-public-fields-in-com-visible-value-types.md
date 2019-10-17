---
title: 'CA1413: Vyhněte se neveřejným polím v hodnotách viditelných modulem COM'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d47a7ff2633b94de73435168136060e741080de7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444192"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: Vyhněte se neveřejným polím v hodnotách viditelných modulem COM

|||
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|Kategorie|Microsoft. interoperabilita|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Typ hodnoty, který je konkrétně označen jako viditelný pro model COM (Component Object Model), deklaruje pole instance NonPublic.

## <a name="rule-description"></a>Popis pravidla
Neveřejná pole instancí hodnotových typů viditelných moduly COM jsou viditelná klientům typu COM. Projděte si obsah pole s informacemi, které by neměly být vystavené nebo které budou mít neúmyslný návrh nebo bezpečnostní účinek.

Ve výchozím nastavení jsou všechny typy veřejné hodnoty viditelné modelu COM. Chcete-li však omezit falešně pozitivní hodnoty, toto pravidlo vyžaduje explicitní stanovení viditelnosti typu modelu COM. Obsahující sestavení musí být označeno s <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> nastavenou na `false` a typ musí být označený jako <xref:System.Runtime.InteropServices.ComVisibleAttribute> nastavený na `true`.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla a ponechat pole skryté, změňte typ hodnoty na typ odkazu nebo odeberte atribut <xref:System.Runtime.InteropServices.ComVisibleAttribute> z typu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Je bezpečné potlačit upozornění od tohoto pravidla, pokud je veřejná expozice pole přijatelná.

## <a name="example"></a>Příklad
Následující příklad ukazuje typ, který je v rozporu s pravidlem.

[!code-csharp[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
[!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]

## <a name="related-rules"></a>Související pravidla
[CA1407: Vyhněte se statickým členům ve viditelných typech modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

[CA1017: Označte sestavení pomocí atributu ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Viz také:

- [Spolupráce s nespravovaným kódem](/dotnet/framework/interop/index)
- [Kvalifikace typů .NET pro spolupráci](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
