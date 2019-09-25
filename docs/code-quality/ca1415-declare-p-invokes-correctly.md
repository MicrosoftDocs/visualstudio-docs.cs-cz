---
title: 'CA1415: Deklarujte správně volání nespravovaných kódů'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99274abee2c05a1bd33e34c9eb02cc928c1b54b0
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234615"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: Deklarujte správně volání nespravovaných kódů

|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|Kategorie|Microsoft. interoperabilita|
|Zásadní změna|Bez přerušení – Pokud volání nespravovaného parametru, které deklaruje parametr, nemůže být mimo sestavení viditelné. Přerušení – Pokud je volání nespravovaného parametru, které deklaruje parametr, se může zobrazit mimo sestavení.|

## <a name="cause"></a>příčina
Metoda Invoke platformy je nesprávně deklarovaná.

## <a name="rule-description"></a>Popis pravidla
Metoda Invoke platformy přistupuje k nespravovanému kódu a je definována pomocí `Declare` klíčového slova v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nebo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. V současné době toto pravidlo hledá deklarace metod vyvolání platformy, které cílí na funkce Win32, které mají ukazatel na překrývající se parametr struktury a odpovídající spravovaný parametr není ukazatel na <xref:System.Threading.NativeOverlapped?displayProperty=fullName> strukturu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, deklarujte správně metodu Invoke platformy.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
Následující příklad ukazuje metody vyvolání platformy, které porušují pravidlo a splňují pravidlo.

[!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]

## <a name="see-also"></a>Viz také:
[Spolupráce s nespravovaným kódem](/dotnet/framework/interop/index)