---
title: 'CA1410: metody registrace modelu COM by se měly shodovat | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 30f507f07de858dc222b4824ac6da633c76812ab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652747"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: Metody registrace modelu COM by si měly odpovídat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|Kategorie|Microsoft. interoperabilita|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Typ deklaruje metodu, která je označena atributem <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>, ale nedeklaruje metodu, která je označena atributem <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> nebo naopak.

## <a name="rule-description"></a>Popis pravidla
 Pro klienty modelu COM (Component Object Model) pro vytváření [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]ho typu musí být nejprve registrován typ. Pokud je k dispozici, metoda, která je označena atributem <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>, je volána během procesu registrace pro spuštění kódu zadaného uživatelem. Odpovídající metoda, která je označena atributem <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>, je volána během procesu zrušení registrace pro vrácení operací registrační metody.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přidejte odpovídající metodu registrace nebo zrušení registrace.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, který je v rozporu s pravidlem. Kód s komentářem zobrazuje opravu porušení.

 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/cs/FxCop.Interoperability.ComRegistration.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/vb/FxCop.Interoperability.ComRegistration.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1411: Metody registrace modelu COM by neměly být viditelné](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>Viz také
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName> [registrace sestavení pomocí modelu COM](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [Regasm. exe (nástroj registrace sestavení)](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)
