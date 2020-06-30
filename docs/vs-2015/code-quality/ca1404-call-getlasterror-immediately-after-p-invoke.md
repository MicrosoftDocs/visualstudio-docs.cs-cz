---
title: 'CA1404: volejte GetLastError hned po volání P-Invoke | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 54ac9a4d56136d9e981ae038a0b219aa4cb4774e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544492"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: Volejte GetLastError ihned po volání nespravovaného kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Kategorie|Microsoft. interoperabilita|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Volání <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> metody nebo ekvivalentní `GetLastError` funkce Win32 a volání, které je bezprostředně předtím, není metodou vyvolání platformy.

## <a name="rule-description"></a>Popis pravidla
 Metoda Invoke platformy přistupuje k nespravovanému kódu a je definována pomocí `Declare` klíčového slova v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] nebo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atributu. Obecně nespravované funkce při selhání volají `SetLastError` funkci Win32, aby nastavily kód chyby, který je přidružen k selhání. Volající funkce, která selhala, volá `GetLastError` funkci Win32 pro načtení kódu chyby a určení příčiny selhání. Kód chyby je udržován na jednotlivých vláknech a je přepsáno dalším voláním `SetLastError` . Po volání metody vyvolání neúspěšné platformy může spravovaný kód získat kód chyby voláním <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> metody. Vzhledem k tomu, že kód chyby může být přepsán interními voláními z jiných metod spravované knihovny tříd, `GetLastError` <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> Metoda nebo by měla být volána ihned po volání metody Invoke platformy.

 Pravidlo ignoruje volání následujících spravovaných členů, pokud k nim dojde mezi voláním metody Invoke platformy a voláním <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> . Tyto členy nemění kód chyby a jsou užitečné pro určení úspěchu některých volání metod vyvolání platformy.

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přesuňte volání, aby <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> hned za voláním metody Invoke platformy.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 V případě, že kód mezi voláním metody Invoke platformy a <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> volání metody nemůže explicitně nebo implicitně způsobit změnu kódu chyby, je bezpečné potlačit upozornění od tohoto pravidla.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, která porušuje pravidlo a metodu, která splňuje pravidlo.

 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/cs/FxCop.Interoperability.LastErrorPInvoke.cs#1)]
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/vb/FxCop.Interoperability.LastErrorPInvoke.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1060: přesunout volání nespravovaného volání do třídy NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: vstupní body volání nespravovaného volání by měly existovat](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: volání nespravovaných kódů by neměla být viditelná](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: Určete zařazování pro argumenty řetězce volání nespravovaného voláním](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205: Použijte spravované ekvivalenty rozhraní Win32 API](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)
