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
ms.openlocfilehash: 85e27ab04ca81f5513a0b09bc41548f4a7c2430d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547677"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Použijte spravované ekvivalenty rozhraní Win32 API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Metoda Invoke platformy je definována a v knihovně tříd existuje metoda s ekvivalentní funkcí [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

## <a name="rule-description"></a>Popis pravidla
 Metoda Invoke platformy se používá k volání nespravované funkce knihovny DLL a je definována pomocí <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atributu nebo `Declare` klíčového slova v Visual Basic. Nesprávně definovaná metoda Invoke platformy může vést k výjimkám za běhu z důvodu problémů, jako je nesprávně pojmenovaná funkce, chybné mapování parametrů a návratové hodnoty datových typů a nesprávných specifikací polí, jako je konvence volání a znaková sada. Je-li k dispozici, je všeobecně jednodušší a méně náchylné k chybám, aby volaly ekvivalentní spravovanou metodu, než pro definování a volání nespravované metody přímo. Volání metody Invoke platformy může také vést k dalším problémům zabezpečení, které je potřeba řešit.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, nahraďte volání nespravované funkce voláním spravovaného ekvivalentu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačí upozornění od tohoto pravidla, pokud navrhovaná metoda nahrazení neposkytuje potřebné funkce.

## <a name="example"></a>Příklad
 Následující příklad ukazuje definici metody vyvolání platformy, která porušuje pravidlo. Kromě toho se zobrazí volání metody Invoke platformy a ekvivalentní spravovaná metoda.

 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/cs/FxCop.Usage.ManagedEquivalents.cs#1)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/vb/FxCop.Usage.ManagedEquivalents.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1404: volejte GetLastError hned po volání nespravovaného volání](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)

 [CA1060: přesunout volání nespravovaného volání do třídy NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: vstupní body volání nespravovaného volání by měly existovat](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: volání nespravovaných kódů by neměla být viditelná](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: Určete zařazování pro argumenty řetězce volání nespravovaného voláním](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)
