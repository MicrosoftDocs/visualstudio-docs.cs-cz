---
title: 'CA1414: označte logické argumenty P-Invoke s MarshalAs | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 588e16a6b21b320ad7012bd20d79a62d027679e3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652694"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Označte logické hodnoty volání nespravovaného kódu pomocí MarshalAs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Kategorie|Microsoft. interoperabilita|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Deklarace metody Invoke platformy zahrnuje parametr <xref:System.Boolean?displayProperty=fullName> nebo návratovou hodnotu, ale atribut <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> se nepoužije na parametr nebo návratovou hodnotu.

## <a name="rule-description"></a>Popis pravidla
 Metoda Invoke platformy přistupuje k nespravovanému kódu a je definována pomocí klíčového slova `Declare` v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] nebo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> určuje chování zařazování, které se používá k převodu datových typů mezi spravovaným a nespravovaným kódem. Mnoho jednoduchých datových typů, například <xref:System.Byte?displayProperty=fullName> a <xref:System.Int32?displayProperty=fullName>, má jednu reprezentaci v nespravovaném kódu a nepožaduje specifikace jejich chování při zařazování; modul CLR (Common Language Runtime) automaticky poskytuje správné chování.

 Datový typ <xref:System.Boolean> má více reprezentace v nespravovaném kódu. Pokud není zadán <xref:System.Runtime.InteropServices.MarshalAsAttribute>, výchozí chování zařazování pro datový typ <xref:System.Boolean> je <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Toto je celé číslo 32, které není vhodné pro všechny okolnosti. Logická reprezentace, která je požadována nespravovanou metodou, by měla být určena a porovnána s odpovídajícím <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType. bool je typ BOOL typu Win32, který je vždy 4 bajty. UnmanagedType. U1 by se měl používat C++ pro `bool` nebo jiné typy s 1 bajtem. Další informace naleznete v tématu [Výchozí zařazování pro logické typy](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, použijte <xref:System.Runtime.InteropServices.MarshalAsAttribute> na parametr <xref:System.Boolean> nebo návratovou hodnotu. Nastavte hodnotu atributu na odpovídající <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo. I v případě, že je vhodné výchozí chování zařazování, je kód snáze udržován v případě, že je chování explicitně zadáno.

## <a name="example"></a>Příklad
 Následující příklad ukazuje dvě metody vyvolání platformy, které jsou označeny příslušnými atributy <xref:System.Runtime.InteropServices.MarshalAsAttribute>.

 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cpp/FxCop.Interoperability.BoolMarshalAs.cpp#1)]
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cs/FxCop.Interoperability.BoolMarshalAs.cs#1)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/vb/FxCop.Interoperability.BoolMarshalAs.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1901: Deklarace volání nespravovaného kódu by měly být přenosné](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: Určete zařazování pro argumenty řetězce volání nespravovaného kódu](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Viz také
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> [Výchozí zařazování pro logické typy](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9) [, které pracují s nespravovaným kódem](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
