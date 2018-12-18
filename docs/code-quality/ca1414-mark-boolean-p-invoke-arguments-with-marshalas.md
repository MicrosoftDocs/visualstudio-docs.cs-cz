---
title: 'CA1414: Označte logické hodnoty volání nespravovaného kódu pomocí MarshalAs'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a5936c07646201ab3988dd7cc792f758ed698063
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548959"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Označte logické hodnoty volání nespravovaného kódu pomocí MarshalAs

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Kategorie|Microsoft.Interoperability|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Vyvolání platformy – metoda obsahuje prohlášení <xref:System.Boolean?displayProperty=fullName> parametr nebo návratovou hodnotu ale <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> atribut není použit parametr nebo návratovou hodnotu.

## <a name="rule-description"></a>Popis pravidla
 Platforma vyvolat metodu přístupy do nespravovaného kódu a je definován pomocí `Declare` – klíčové slovo v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nebo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Určuje chování zařazování, který se používá k převodu datových typů mezi spravovaným a nespravovaným kódem. Mnoho jednoduché datové typy, jako <xref:System.Byte?displayProperty=fullName> a <xref:System.Int32?displayProperty=fullName>, mají jednotné vyjádření v nespravovaném kódu a nevyžadují specifikace jejich chování zařazování, modul common language runtime automaticky poskytuje správné chování.

 <xref:System.Boolean> Datový typ má více reprezentací v nespravovaném kódu. Když <xref:System.Runtime.InteropServices.MarshalAsAttribute> není zadán, výchozí chování pro zařazování <xref:System.Boolean> datový typ je <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Toto je 32bitové celé číslo, které není vhodné za všech okolností. Logickou reprezentaci, který vyžaduje metodu nespravované by měl určit a spárují s odpovídající <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType.Bool je typ Win32 BOOL, který je vždycky 4 bajty. UnmanagedType.U1 byste měli použít pro C++ `bool` nebo jiných typů 1 bajt.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, použijte <xref:System.Runtime.InteropServices.MarshalAsAttribute> k <xref:System.Boolean> parametr nebo návratovou hodnotu. Nastavit hodnotu atributu na příslušné <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo. I v případě, že výchozí chování zařazování je vhodné, kód je snadněji nepoužije, když je chování explicitně zadán.

## <a name="example"></a>Příklad

Následující příklad ukazuje metody, které jsou označené odpovídající vyvolání platformy <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributy.

 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>Související pravidla
 [CA1901: Deklarace volání nespravovaného kódu by měly být přenosné](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: Určete zařazování pro argumenty řetězce volání nespravovaného kódu](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>
- [Spolupráce s nespravovaným kódem](/dotnet/framework/interop/index)