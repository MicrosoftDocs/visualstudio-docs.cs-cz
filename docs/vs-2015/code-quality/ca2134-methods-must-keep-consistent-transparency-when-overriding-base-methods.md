---
title: 'CA2134: metody musí při přepisování základních metod zachovávat konzistentní transparentnost | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 96910ffc53e6c48f930232c83d87570f1bc71e00
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72608925"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: Metody musejí při přepisování základních metod zachovávat konzistentní transparentnost
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Toto pravidlo je vyvoláno, pokud metoda označená pomocí <xref:System.Security.SecurityCriticalAttribute> přepisuje metodu, která je průhledná nebo označená <xref:System.Security.SecuritySafeCriticalAttribute>. Pravidlo se aktivuje také v případě, že metoda, která je průhledná nebo označená pomocí <xref:System.Security.SecuritySafeCriticalAttribute> přepisuje metodu, která je označená <xref:System.Security.SecurityCriticalAttribute>.

 Pravidlo je použito při přepisování virtuální metody nebo implementaci rozhraní.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo je vyvoláno při pokusech o změnu přístupnosti zabezpečení metody v rámci řetězce dědičnosti. Například pokud je virtuální metoda v základní třídě transparentní nebo bezpečná, pak musí být odvozená třída popsána transparentní nebo bezpečnou metodou. Naopak, pokud je virtuální z hlediska zabezpečení kritická, musí odvozená třída tuto třídu přepsat metodou kritické pro zabezpečení. Stejné pravidlo platí pro implementaci metod rozhraní.

 Pravidla transparentnosti jsou vynutila, pokud je kód zkompilován kompilátorem JIT namísto za běhu, takže výpočet transparentnosti neobsahuje dynamické informace o typu. Proto je možné výsledek výpočtu transparentnosti určit výhradně ze statických typů, které jsou kompilovány JIT, bez ohledu na dynamický typ.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte transparentnost metody, která přepisuje virtuální metodu nebo implementuje rozhraní, aby odpovídala průhlednosti metody Virtual nebo rozhraní.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit upozornění z tohoto pravidla Porušení tohoto pravidla budou mít za následek <xref:System.TypeLoadException> modulu runtime pro sestavení, která používají transparentnost úrovně 2.

## <a name="examples"></a>Příklady

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency/cs/ca2134 - methodsmustoverridewithconsistenttransparency.cs#1)]

## <a name="see-also"></a>Viz také
 [Kód transparentní pro zabezpečení, úroveň 2](https://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)
