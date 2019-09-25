---
title: 'CA1400: Vstupní body volání nespravovaného kódu by měly existovat'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5503f00995a4720207ea0ea9c29201d379e70adb
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234907"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: Vstupní body volání nespravovaného kódu by měly existovat

|||
|-|-|
|TypeName|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|Kategorie|Microsoft. interoperabilita|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Veřejná nebo chráněná metoda je označena atributem <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Nespravovanou knihovnu nelze nalézt nebo nelze metodu porovnat s funkcí v knihovně. Pokud pravidlo nemůže najít název metody přesně tak, jak je zadán, vyhledá verze ANSI nebo roztažitelné znaků metodou pomocí přípony názvu metody s "A" nebo "W". Pokud není nalezena žádná shoda, pravidlo se pokusí najít funkci pomocí formátu názvu __stdcall (_MyMethod@12, kde 12 představuje délku argumentů). Pokud se nenajde žádná shoda a název metody začíná znakem "#", pravidlo vyhledá funkci jako odkaz na ordinální místo odkaz na název.

## <a name="rule-description"></a>Popis pravidla
Není k dispozici žádná kontrolní doba kompilace, aby bylo zajištěno, že metody <xref:System.Runtime.InteropServices.DllImportAttribute> , které jsou označeny, jsou umístěny v odkazované nespravované knihovně DLL. Není-li v knihovně žádná funkce, která má zadaný název, nebo argumenty metody neodpovídají argumentům funkce, modul CLR vyvolá výjimku.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, opravte metodu, která má <xref:System.Runtime.InteropServices.DllImportAttribute> atribut. Ujistěte se, že nespravované knihovny existují a jsou ve stejném adresáři jako sestavení, které obsahuje metodu. Pokud je knihovna přítomna a správně odkazována, ověřte, zda název metody, návratový typ a signatura argumentu odpovídají funkci knihovny.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Potlačit upozornění z tohoto pravidla, pokud je nespravovaná knihovna ve stejném adresáři jako spravované sestavení, které na něj odkazuje. Může být bezpečné potlačit upozornění z tohoto pravidla v případě, že nespravovanou knihovnu nelze najít.

## <a name="example"></a>Příklad
Následující příklad ukazuje typ, který je v rozporu s pravidlem. V knihovně Kernel32. dll `DoSomethingUnmanaged` není k dispozici žádná funkce s názvem.

[!code-csharp[FxCop.Interoperability.DLLExists#1](../code-quality/codesnippet/CSharp/ca1400-p-invoke-entry-points-should-exist_1.cs)]

## <a name="see-also"></a>Viz také:
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>