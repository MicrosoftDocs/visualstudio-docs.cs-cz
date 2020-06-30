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
ms.openlocfilehash: 783f7fad05cad18efea2f83b6d76c4c9e644f119
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548379"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Označte logické hodnoty volání nespravovaného kódu pomocí MarshalAs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Kategorie|Microsoft. interoperabilita|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Deklarace metody Invoke platformy obsahuje <xref:System.Boolean?displayProperty=fullName> parametr nebo návratovou hodnotu, ale <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> atribut není aplikován na parametr nebo návratovou hodnotu.

## <a name="rule-description"></a>Popis pravidla
 Metoda Invoke platformy přistupuje k nespravovanému kódu a je definována pomocí `Declare` klíčového slova v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] nebo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> . <xref:System.Runtime.InteropServices.MarshalAsAttribute>Určuje chování zařazování, které se používá k převodu datových typů mezi spravovaným a nespravovaným kódem. Mnoho jednoduchých datových typů, jako jsou <xref:System.Byte?displayProperty=fullName> a <xref:System.Int32?displayProperty=fullName> , mají jedinou reprezentaci v nespravovaném kódu a nevyžadují specifikaci jejich chování při zařazování. modul CLR (Common Language Runtime) automaticky doplní správné chování.

 <xref:System.Boolean>Datový typ obsahuje více reprezentace v nespravovaném kódu. Pokud není <xref:System.Runtime.InteropServices.MarshalAsAttribute> zadán, výchozí chování zařazování pro <xref:System.Boolean> datový typ je <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> . Toto je celé číslo 32, které není vhodné pro všechny okolnosti. Logická reprezentace, která je požadována nespravovanou metodou, by měla být určena a porovnána s odpovídajícími <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> . UnmanagedType. bool je typ BOOL typu Win32, který je vždy 4 bajty. UnmanagedType. U1 by se měl používat pro C++ `bool` nebo jiné typy s 1 bajtem. Další informace naleznete v tématu [Výchozí zařazování pro logické typy](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, použijte <xref:System.Runtime.InteropServices.MarshalAsAttribute> <xref:System.Boolean> parametr nebo vrácenou hodnotu. Nastavte hodnotu atributu na odpovídající <xref:System.Runtime.InteropServices.UnmanagedType> .

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo. I v případě, že je vhodné výchozí chování zařazování, je kód snáze udržován v případě, že je chování explicitně zadáno.

## <a name="example"></a>Příklad
 Následující příklad ukazuje dvě metody vyvolání platformy, které jsou označeny odpovídajícími <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributy.

 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cpp/FxCop.Interoperability.BoolMarshalAs.cpp#1)]
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cs/FxCop.Interoperability.BoolMarshalAs.cs#1)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/vb/FxCop.Interoperability.BoolMarshalAs.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1901: deklarace P/Invoke by měly být přenosné](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: Určete zařazování pro argumenty řetězce volání nespravovaného voláním](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Viz také
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>[Výchozí zařazování pro logické typy](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9) [, které pracují s nespravovaným kódem](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
