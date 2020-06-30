---
title: 'CA1406: Vyhněte se argumentům Int64 pro Visual Basic 6 klientů | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b6ab93c24cd97d498ae886c7a9184fd4a5f111f1
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534911"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Vyhněte se argumentům Int64 pro klienty jazyka Visual Basic 6
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|Kategorie|Microsoft. interoperabilita|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Typ, který je konkrétně označen jako viditelný pro model COM (Component Object Model), deklaruje člen, který přijímá <xref:System.Int64?displayProperty=fullName> argument.

## <a name="rule-description"></a>Popis pravidla
 Klienti modelu COM Visual Basic 6 nemají přístup k 64 celých čísel.

 Ve výchozím nastavení jsou následující prvky viditelné v modelu COM: sestavení, veřejné typy, členy veřejné instance ve veřejných typech a všechny členy typů veřejné hodnoty. Chcete-li však omezit falešně pozitivní hodnoty, toto pravidlo vyžaduje explicitní zadání viditelnosti typu COM; obsahující sestavení musí být označeno <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> nastavením na `false` a typ musí být označen <xref:System.Runtime.InteropServices.ComVisibleAttribute> nastavením na `true` .

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla pro parametr, jehož hodnota může být vždy vyjádřena jako 32 bitová integrál, změňte typ parametru na <xref:System.Int32?displayProperty=fullName> . Pokud hodnota parametru může být větší, než může být vyjádřena jako 32-bit integrál, změňte typ parametru na <xref:System.Decimal?displayProperty=fullName> . Všimněte si, že obě <xref:System.Single?displayProperty=fullName> a <xref:System.Double?displayProperty=fullName> ztrácejí přesnost v horních rozsahech <xref:System.Int64> datového typu. Pokud člen nemá být viditelný pro model COM, označte jej pomocí příkazu <xref:System.Runtime.InteropServices.ComVisibleAttribute> set to `false` .

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Z tohoto pravidla je bezpečné potlačit upozornění, pokud je jisté, že Visual Basic 6 klientů modelu COM nebude přistupovat k tomuto typu.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, který je v rozporu s pravidlem.

 [!code-csharp[FxCop.Interoperability.LongArgument#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/cs/FxCop.Interoperability.LongArgument.cs#1)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/vb/FxCop.Interoperability.LongArgument.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1413: Vyhněte se neveřejným polím v typech hodnot viditelných modulem COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Vyhněte se statickým členům ve viditelných typech modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Označte sestavení pomocí ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Viz také
 Spolupráce s [datovým typem Long](https://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516) [nespravovaného kódu](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
