---
title: 'CA2205: použijte spravované ekvivalenty Win32 API | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 931b1e5099bf221fefc7a8f4a19524d2531a4418
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609490"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Použijte spravované ekvivalenty rozhraní Win32 API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>příčina
 Metoda Invoke platformy je definována a v knihovně tříd [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] existuje metoda s ekvivalentní funkcí.

## <a name="rule-description"></a>Popis pravidla
 Metoda Invoke platformy se používá k volání nespravované funkce knihovny DLL a je definována pomocí atributu <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> nebo klíčového slova `Declare` v Visual Basic. Nesprávně definovaná metoda Invoke platformy může vést k výjimkám za běhu z důvodu problémů, jako je nesprávně pojmenovaná funkce, chybné mapování parametrů a návratové hodnoty datových typů a nesprávných specifikací polí, jako je konvence volání a znak. stanovenými. Je-li k dispozici, je všeobecně jednodušší a méně náchylné k chybám, aby volaly ekvivalentní spravovanou metodu, než pro definování a volání nespravované metody přímo. Volání metody Invoke platformy může také vést k dalším problémům zabezpečení, které je potřeba řešit.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, nahraďte volání nespravované funkce voláním spravovaného ekvivalentu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačí upozornění od tohoto pravidla, pokud navrhovaná metoda nahrazení neposkytuje potřebné funkce.

## <a name="example"></a>Příklad
 Následující příklad ukazuje definici metody vyvolání platformy, která porušuje pravidlo. Kromě toho se zobrazí volání metody Invoke platformy a ekvivalentní spravovaná metoda.

 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/cs/FxCop.Usage.ManagedEquivalents.cs#1)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/vb/FxCop.Usage.ManagedEquivalents.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1404: Volejte GetLastError ihned po volání nespravovaného kódu](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)

 [CA1060: Přesuňte volání nespravovaných kódů do třídy NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: Vstupní body volání nespravovaného kódu by měly existovat](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: Volání nespravovaných kódů by neměla být viditelná](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: Určete zařazování pro argumenty řetězce volání nespravovaného kódu](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)
