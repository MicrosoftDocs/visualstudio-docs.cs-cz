---
title: 'CA2205: Použijte spravované ekvivalenty rozhraní Win32 API | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ba23b176ed4f2120f4675611567955bdaf652153
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49907466"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Použijte spravované ekvivalenty rozhraní Win32 API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Kategorie|Microsoft.Usage|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina
 Vyvolání platformy je definována metoda a metoda s ekvivalentní funkce nachází [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] knihovny tříd.

## <a name="rule-description"></a>Popis pravidla
 Vyvolání platformy metodu lze volat nespravovanou funkci knihovny DLL a je definován pomocí <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atribut, nebo `Declare` – klíčové slovo v jazyce Visual Basic. Nesprávně definovaná platformu vyvolání metody může vést k výjimky modulu CLR z důvodu problémy, jako je misnamed funkce vadným mapování parametrů a návratové hodnoty datových typů a specifikace nesprávná pole, jako je konvence volání a znak Nastavte. Pokud je k dispozici, je obvykle jednodušší a méně náchylný k volání metody ekvivalentní spravované než definovat a volat metodu nespravované přímo. Volání na platformě volání metody může také vést k další bezpečnostní problémy, které musí vzít.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, nahraďte volání nespravovanou funkci voláním ekvivalentní spravované.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit upozornění tohoto pravidla, pokud metoda navrhované nahrazení neposkytuje potřebné funkce.

## <a name="example"></a>Příklad
 Následující příklad ukazuje a platformu vyvolání definici metody, která porušuje pravidla. Kromě toho vyvolat metodu volání na platformu a ekvivalentní spravované metody jsou zobrazeny.

 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/cs/FxCop.Usage.ManagedEquivalents.cs#1)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/vb/FxCop.Usage.ManagedEquivalents.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1404: Volejte GetLastError ihned po volání nespravovaného kódu](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)

 [CA1060: Přesuňte volání nespravovaných kódů do třídy NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: Vstupní body volání nespravovaného kódu by měly existovat](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: Volání nespravovaných kódů by neměla být viditelná](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: Určete zařazování pro argumenty řetězce volání nespravovaného kódu](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)



