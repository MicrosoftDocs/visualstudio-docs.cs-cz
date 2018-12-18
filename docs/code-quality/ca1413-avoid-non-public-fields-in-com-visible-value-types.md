---
title: 'CA1413: Vyhněte se neveřejným polím v hodnotách viditelných modulem COM'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 060d8ebd26b08ef02a9986846bdab2a25a85072f
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547903"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: Vyhněte se neveřejným polím v hodnotách viditelných modulem COM

|||
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|Kategorie|Microsoft.Interoperability|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Hodnotový typ, který je označen jako viditelný pro Model COM (Component Object) deklaruje instanci neveřejné pole.

## <a name="rule-description"></a>Popis pravidla
 Neveřejná pole instancí hodnotových typů viditelných moduly COM jsou viditelná klientům typu COM. Zkontrolujte obsah pole informace, které by neměly být vystaveny nebo které budou mít nežádoucí vliv návrh nebo zabezpečení.

 Všechny veřejné hodnotové typy jsou standardně viditelné v modelu COM. Pokud chcete snížit počet falešně pozitivních výsledků, vyžaduje toto pravidlo viditelnost modelu COM typ, který má být explicitně uvedena. Musí být označené obsahující sestavení <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> nastavena na `false` a typ musí být označeny pomocí <xref:System.Runtime.InteropServices.ComVisibleAttribute> nastavena na `true`.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla a ponechat skryté pole, změňte typ hodnoty na typ odkazu nebo odebrat <xref:System.Runtime.InteropServices.ComVisibleAttribute> atribut typu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění tohoto pravidla, pokud veřejná odhalení pole je přijatelné.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, který porušuje pravidla.

 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]

## <a name="related-rules"></a>Související pravidla
 [CA1407: Vyhněte se statickým členům ve viditelných typech modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Označte sestavení pomocí atributu ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Viz také:

- [Spolupráce s nespravovaným kódem](/dotnet/framework/interop/index)
- [Kvalifikace typů .NET pro spolupráci](/dotnet/framework/interop/qualifying-net-types-for-interoperation)