---
title: 'CA1404: Volejte GetLastError ihned po volání nespravovaného kódu'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a6876d9e9326d67d781f49e69a65d41284f54da8
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444273"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: Volejte GetLastError ihned po volání nespravovaného kódu

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Kategorie|Microsoft. interoperabilita|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Bylo provedeno volání metody <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> nebo ekvivalentní funkce Win32 `GetLastError` a volání, které je bezprostředně předtím, nikoli metodou vyvolání platformy.

## <a name="rule-description"></a>Popis pravidla
Metoda Invoke platformy přistupuje k nespravovanému kódu a je definována pomocí klíčového slova `Declare` v atributu [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nebo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Obecně platí, že po selhání nespravované funkce volají funkci Win32 `SetLastError` pro nastavení kódu chyby, který je přidružen k selhání. Volající funkce, která selhala, volá funkci Win32 `GetLastError`, která načte kód chyby a určí příčinu selhání. Kód chyby je udržován v závislosti na vlákně a je přepsáno dalším voláním `SetLastError`. Po volání metody vyvolání neúspěšné platformy může spravovaný kód získat kód chyby voláním metody <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Vzhledem k tomu, že kód chyby může být přepsán interními voláními z jiných metod spravované knihovny tříd, metoda `GetLastError` nebo <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> by měla být volána ihned po volání metody Invoke platformy.

Pravidlo ignoruje volání následujících spravovaných členů, pokud k nim dojde mezi voláním metody Invoke platformy a voláním <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Tyto členy nemění kód chyby a jsou užitečné pro určení úspěchu některých volání metod vyvolání platformy.

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, přesuňte volání <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> tak, aby hned za voláním metody Invoke platformy.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
V případě, že kód mezi voláním metody Invoke platformy a volání metody <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> nemůže explicitně nebo implicitně způsobit změnu kódu chyby, je bezpečné potlačit upozornění od tohoto pravidla.

## <a name="example"></a>Příklad
Následující příklad ukazuje metodu, která porušuje pravidlo a metodu, která splňuje pravidlo.

[!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
[!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]

## <a name="related-rules"></a>Související pravidla
[CA1060: Přesuňte volání nespravovaných kódů do třídy NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

[CA1400: Vstupní body volání nespravovaného kódu by měly existovat](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

[CA1401: Volání nespravovaných kódů by neměla být viditelná](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

[CA2101: Určete zařazování pro argumenty řetězce volání nespravovaného kódu](../code-quality/ca2101.md)

[CA2205: Použijte spravované ekvivalenty rozhraní Win32 API](../code-quality/ca2205.md)
