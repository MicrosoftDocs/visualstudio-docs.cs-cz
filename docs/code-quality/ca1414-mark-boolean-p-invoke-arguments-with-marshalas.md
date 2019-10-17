---
title: 'CA1414: Označte logické hodnoty volání nespravovaného kódu pomocí MarshalAs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0f8140e78d1ee3340e9ee5441e183b55d4c5111c
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444168"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Označte logické hodnoty volání nespravovaného kódu pomocí MarshalAs

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Kategorie|Microsoft. interoperabilita|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Deklarace metody Invoke platformy zahrnuje parametr <xref:System.Boolean?displayProperty=fullName> nebo návratovou hodnotu, ale atribut <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> se nepoužije na parametr nebo návratovou hodnotu.

## <a name="rule-description"></a>Popis pravidla
Metoda Invoke platformy přistupuje k nespravovanému kódu a je definována pomocí klíčového slova `Declare` v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nebo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> určuje chování zařazování, které se používá k převodu datových typů mezi spravovaným a nespravovaným kódem. Mnoho jednoduchých datových typů, například <xref:System.Byte?displayProperty=fullName> a <xref:System.Int32?displayProperty=fullName>, má jednu reprezentaci v nespravovaném kódu a nepožaduje specifikace jejich chování při zařazování; modul CLR (Common Language Runtime) automaticky poskytuje správné chování.

Datový typ <xref:System.Boolean> má více reprezentace v nespravovaném kódu. Pokud není zadán <xref:System.Runtime.InteropServices.MarshalAsAttribute>, výchozí chování zařazování pro datový typ <xref:System.Boolean> je <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Toto je celé číslo 32, které není vhodné pro všechny okolnosti. Logická reprezentace, která je požadována nespravovanou metodou, by měla být určena a porovnána s odpovídajícím <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType. bool je typ BOOL typu Win32, který je vždy 4 bajty. UnmanagedType. U1 by se měl používat C++ pro `bool` nebo jiné typy s 1 bajtem.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, použijte <xref:System.Runtime.InteropServices.MarshalAsAttribute> na parametr <xref:System.Boolean> nebo návratovou hodnotu. Nastavte hodnotu atributu na odpovídající <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo. I v případě, že je vhodné výchozí chování zařazování, je kód snáze udržován v případě, že je chování explicitně zadáno.

## <a name="example"></a>Příklad

Následující příklad ukazuje metody vyvolání platformy, které jsou označeny příslušnými atributy <xref:System.Runtime.InteropServices.MarshalAsAttribute>.

[!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
[!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
[!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>Související pravidla
[CA1901: Deklarace volání nespravovaného kódu by měly být přenosné](../code-quality/ca1901.md)

[CA2101: Určete zařazování pro argumenty řetězce volání nespravovaného kódu](../code-quality/ca2101.md)

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>
- [Spolupráce s nespravovaným kódem](/dotnet/framework/interop/index)
