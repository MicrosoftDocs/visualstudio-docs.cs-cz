---
title: 'CA2205: Použijte spravované ekvivalenty rozhraní Win32 API'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ad26dcbbbef5a34796ca0aa134653c3c9df5d763
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253261"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Použijte spravované ekvivalenty rozhraní Win32 API

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Kategorie|Microsoft.Usage|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Metoda Invoke platformy je definována a v rozhraní .NET existuje metoda s ekvivalentními funkcemi.

## <a name="rule-description"></a>Popis pravidla

Metoda Invoke platformy se používá k volání nespravované funkce knihovny DLL a je definována pomocí <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atributu `Declare` nebo klíčového slova v Visual Basic. Nesprávně definovaná metoda Invoke platformy může vést k výjimkám za běhu, protože došlo k problémům, jako je například nesprávně pojmenovaná funkce, chybné mapování parametrů a návratové hodnoty datových typů a nesprávné specifikace polí, jako je konvence volání a znak. stanovenými. Je-li k dispozici, je jednodušší a méně náchylná k chybám pro volání ekvivalentní spravované metody, než pro definování a volání nespravované metody přímo. Volání metody Invoke platformy může také vést k dalším problémům zabezpečení, které je potřeba řešit.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, nahraďte volání nespravované funkce voláním spravovaného ekvivalentu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Potlačí upozornění od tohoto pravidla, pokud navrhovaná metoda nahrazení neposkytuje potřebné funkce.

## <a name="example"></a>Příklad

Následující příklad ukazuje definici metody vyvolání platformy, která porušuje pravidlo. Kromě toho se zobrazí volání metody Invoke platformy a ekvivalentní spravovaná metoda.

[!code-csharp[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
[!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]

## <a name="related-rules"></a>Související pravidla

- [CA1404: Zavolat GetLastError hned po volání nespravovaného volání](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)
- [CA1060: Přesunout volání nespravovaného volání do třídy NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)
- [CA1400: Vstupní body volání nespravovaného volání by měly existovat](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)
- [CA1401: Volání nespravovaných kódů by neměla být viditelná](../code-quality/ca1401-p-invokes-should-not-be-visible.md)
- [CA2101: Zadat zařazování pro argumenty řetězce volání nespravovaného volání](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)