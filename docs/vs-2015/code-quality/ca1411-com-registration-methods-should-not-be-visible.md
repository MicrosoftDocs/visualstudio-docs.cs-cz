---
title: 'CA1411: metody registrace modelu COM by neměly být viditelné | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f3ddd2c90d23884bd08a90560dcc5ed0fe700aaf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652717"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: Metody registrace modelu COM by neměly být viditelné
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|Kategorie|Microsoft. interoperabilita|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Metoda, která je označena atributem <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> nebo atributem <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>, je externě viditelná.

## <a name="rule-description"></a>Popis pravidla
 Pokud je sestavení registrováno pomocí modelu COM (Component Object Model), položky jsou přidány do registru pro každý typ viditelný v sestavení. Metody označené atributem <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> a <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> jsou volány během procesu registrace a zrušení registrace, v uvedeném pořadí, ke spuštění uživatelského kódu, který je specifický pro registraci nebo zrušení registrace těchto typů. Tento kód by neměl být volán mimo tyto procesy.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte přístupnost metody na `private` nebo `internal` (`Friend` v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje dvě metody, které porušují pravidlo.

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/cs/FxCop.Interoperability.ComRegistration2.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/vb/FxCop.Interoperability.ComRegistration2.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1410: Metody registrace modelu COM by si měly odpovídat](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>Viz také
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName> [registrace sestavení pomocí modelu COM](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [Regasm. exe (nástroj registrace sestavení)](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)
