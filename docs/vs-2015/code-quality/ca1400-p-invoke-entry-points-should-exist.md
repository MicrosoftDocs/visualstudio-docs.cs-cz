---
title: 'CA1400: vstupní body volání nespravovaného volání by měly existovat | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 15b63e49f89e17db631772c48765cc610f47ed29
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548301"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: Vstupní body volání nespravovaného kódu by měly existovat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|Kategorie|Microsoft. interoperabilita|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Veřejná nebo chráněná metoda je označena atributem <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> . Nespravovanou knihovnu nelze nalézt nebo nelze metodu porovnat s funkcí v knihovně. Pokud pravidlo nemůže najít název metody přesně tak, jak je zadán, vyhledá verze ANSI nebo roztažitelné znaků metodou pomocí přípony názvu metody s "A" nebo "W". Pokud není nalezena žádná shoda, pravidlo se pokusí najít funkci pomocí formátu názvu __stdcall ( _MyMethod@12 , kde 12 představuje délku argumentů). Pokud se nenajde žádná shoda a název metody začíná znakem "#", pravidlo vyhledá funkci jako odkaz na ordinální místo odkaz na název.

## <a name="rule-description"></a>Popis pravidla
 Není k dispozici žádná kontrolní doba kompilace, aby bylo zajištěno, že metody, které jsou označeny, <xref:System.Runtime.InteropServices.DllImportAttribute> jsou umístěny v odkazované nespravované knihovně DLL. Není-li v knihovně žádná funkce, která má zadaný název, nebo argumenty metody neodpovídají argumentům funkce, modul CLR vyvolá výjimku.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, opravte metodu, která má <xref:System.Runtime.InteropServices.DllImportAttribute> atribut. Ujistěte se, že nespravované knihovny existují a jsou ve stejném adresáři jako sestavení, které obsahuje metodu. Pokud je knihovna přítomna a správně odkazována, ověřte, zda název metody, návratový typ a signatura argumentu odpovídají funkci knihovny.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit upozornění z tohoto pravidla, pokud je nespravovaná knihovna ve stejném adresáři jako spravované sestavení, které na něj odkazuje. Může být bezpečné potlačit upozornění z tohoto pravidla v případě, že nespravovanou knihovnu nelze najít.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, který je v rozporu s pravidlem. V kernel32.dll není k dispozici žádná funkce s názvem `DoSomethingUnmanaged` .

 [!code-csharp[FxCop.Interoperability.DLLExists#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DLLExists/cs/FxCop.Interoperability.DLLExists.cs#1)]

## <a name="see-also"></a>Viz také
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>
