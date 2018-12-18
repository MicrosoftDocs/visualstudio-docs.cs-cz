---
title: 'CA2205: Použijte spravované ekvivalenty rozhraní Win32 API'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 8c88feb35a4699770b7a05a266168e0c3ad347e4
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2018
ms.locfileid: "47860111"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Použijte spravované ekvivalenty rozhraní Win32 API

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Kategorie|Microsoft.Usage|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina

Vyvolání platformy je definována metoda a metodu s ekvivalentní funkce v knihovně tříd rozhraní .NET Framework existuje.

## <a name="rule-description"></a>Popis pravidla

Vyvolání platformy metodu lze volat nespravovanou funkci knihovny DLL a je definován pomocí <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atribut, nebo `Declare` – klíčové slovo v jazyce Visual Basic. Nesprávně definovaná platformu vyvolání metody může vést k výjimky modulu CLR z důvodu problémy, jako je misnamed funkce vadným mapování parametrů a návratové hodnoty datových typů a specifikace nesprávná pole, jako je konvence volání a znak Nastavte. Pokud je k dispozici, je jednodušší a méně náchylný k volání metody ekvivalentní spravované než definovat a volat metodu nespravované přímo. Volání na platformě volání metody může také vést k další bezpečnostní problémy, které musí vzít.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

Chcete-li opravit porušení tohoto pravidla, nahraďte volání nespravovanou funkci voláním ekvivalentní spravované.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Potlačit upozornění tohoto pravidla, pokud metoda navrhované nahrazení neposkytuje potřebné funkce.

## <a name="example"></a>Příklad

Následující příklad ukazuje a platformu vyvolání definici metody, která porušuje pravidla. Kromě toho vyvolat metodu volání na platformu a ekvivalentní spravované metody jsou zobrazeny.

[!code-csharp[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
[!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]

## <a name="related-rules"></a>Související pravidla

- [CA1404: Volejte GetLastError ihned po volání nespravovaného kódu](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)
- [CA1060: Přesuňte volání nespravovaných kódů do třídy NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)
- [CA1400: Vstupní body volání nespravovaného kódu by měly existovat](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)
- [CA1401: Volání nespravovaných kódů by neměla být viditelná](../code-quality/ca1401-p-invokes-should-not-be-visible.md)
- [CA2101: Určete zařazování pro argumenty řetězce volání nespravovaného kódu](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)