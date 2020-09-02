---
title: 'CA1415: deklarace P-vyvolání je správně | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b9931d29c818d95785146558637c32237e2c5276
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547846"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: Deklarujte správně volání nespravovaných kódů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|Kategorie|Microsoft. interoperabilita|
|Narušující změna|Bez přerušení – Pokud volání nespravovaného parametru, které deklaruje parametr, nemůže být mimo sestavení viditelné. Přerušení – Pokud je volání nespravovaného parametru, které deklaruje parametr, se může zobrazit mimo sestavení.|

## <a name="cause"></a>Příčina
 Metoda Invoke platformy je nesprávně deklarovaná.

## <a name="rule-description"></a>Popis pravidla
 Metoda Invoke platformy přistupuje k nespravovanému kódu a je definována pomocí `Declare` klíčového slova v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] nebo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> . V současné době toto pravidlo hledá deklarace metod vyvolání platformy, které cílí na funkce Win32, které mají ukazatel na překrývající se parametr struktury a odpovídající spravovaný parametr není ukazatel na <xref:System.Threading.NativeOverlapped?displayProperty=fullName> strukturu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, deklarujte správně metodu Invoke platformy.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metody vyvolání platformy, které porušují pravidlo a splňují pravidlo.

 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DeclarePInvokes/cs/FxCop.Interoperability.DeclarePInvokes.cs#1)]

## <a name="see-also"></a>Viz také
 [Spolupráce s nespravovaným kódem](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
