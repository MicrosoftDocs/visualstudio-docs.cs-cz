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
ms.openlocfilehash: 8ee4c74fa57811a7f5484dba4b2c3fa27a74437f
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72443982"
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
Metoda Invoke platformy přistupuje k nespravovanému kódu a je definována pomocí klíčového slova `Declare` v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nebo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. V současné době toto pravidlo vyhledá deklarace metod vyvolání platformy, které cílí na funkce Win32, které mají ukazatel na překrývající se parametr struktury a odpovídající spravovaný parametr není ukazatel na strukturu <xref:System.Threading.NativeOverlapped?displayProperty=fullName>.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, deklarujte správně metodu Invoke platformy.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
Následující příklad ukazuje metody vyvolání platformy, které porušují pravidlo a splňují pravidlo.

[!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]

## <a name="see-also"></a>Viz také:
[Spolupráce s nespravovaným kódem](/dotnet/framework/interop/index)
