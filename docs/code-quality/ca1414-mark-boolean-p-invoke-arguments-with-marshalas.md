---
title: 'CA1414: Označte logické argumenty volání nespravovaného kódu pomocí MarshalAs'
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
ms.openlocfilehash: 22e62a1e3209399be4b10a3ec28db4afdd6f0f20
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234677"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Označte logické argumenty volání nespravovaného kódu pomocí MarshalAs

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Kategorie|Microsoft. interoperabilita|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Deklarace metody Invoke platformy obsahuje <xref:System.Boolean?displayProperty=fullName> parametr nebo návratovou hodnotu, <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> ale atribut není aplikován na parametr nebo návratovou hodnotu.

## <a name="rule-description"></a>Popis pravidla
Metoda Invoke platformy přistupuje k nespravovanému kódu a je definována pomocí `Declare` klíčového slova v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nebo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute>Určuje chování zařazování, které se používá k převodu datových typů mezi spravovaným a nespravovaným kódem. Mnoho jednoduchých datových typů, jako <xref:System.Byte?displayProperty=fullName> jsou a <xref:System.Int32?displayProperty=fullName>, mají jedinou reprezentaci v nespravovaném kódu a nevyžadují specifikaci jejich chování při zařazování. modul CLR (Common Language Runtime) automaticky doplní správné chování.

<xref:System.Boolean> Datový typ obsahuje více reprezentace v nespravovaném kódu. Pokud není zadán, výchozí chování zařazování <xref:System.Boolean> pro datový typ je <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Toto je celé číslo 32, které není vhodné pro všechny okolnosti. Logická reprezentace, která je požadována nespravovanou metodou, by měla být určena a porovnána s <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>odpovídajícími. UnmanagedType. bool je typ BOOL typu Win32, který je vždy 4 bajty. UnmanagedType. U1 by se měl použít C++ `bool` pro nebo jiné typy s 1 bajtem.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, použijte <xref:System.Runtime.InteropServices.MarshalAsAttribute> <xref:System.Boolean> parametr nebo vrácenou hodnotu. Nastavte hodnotu atributu na odpovídající <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo. I v případě, že je vhodné výchozí chování zařazování, je kód snáze udržován v případě, že je chování explicitně zadáno.

## <a name="example"></a>Příklad

Následující příklad ukazuje metody vyvolání platformy, které jsou označeny odpovídajícími <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributy.

[!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
[!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
[!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>Související pravidla
[CA1901: Deklarace P/Invoke by měly být přenosné](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

[CA2101: Zadat zařazování pro argumenty řetězce volání nespravovaného volání](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>
- [Spolupráce s nespravovaným kódem](/dotnet/framework/interop/index)