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
ms.openlocfilehash: 43767ce04b32440a5c6753f5bfcabb91487c1232
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546702"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: Metody registrace modelu COM by si měly odpovídat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|Kategorie|Microsoft. interoperabilita|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Typ deklaruje metodu, která je označena <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> atributem, ale nedeklaruje metodu, která je označena <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atributem, nebo naopak.

## <a name="rule-description"></a>Popis pravidla
 Pro klienty modelu COM (Component Object Model) pro vytvoření [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] typu musí být nejprve registrován typ. Je-li k dispozici, metoda, která je označena <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> atributem, je volána během procesu registrace pro spuštění kódu zadaného uživatelem. Odpovídající metoda, která je označena <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> atributem, je volána během procesu zrušení registrace pro vrácení operací registrační metody.

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
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>[Registrace sestavení pomocí modelu COM](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [Regasm.exe (nástroj registrace sestavení)](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)
