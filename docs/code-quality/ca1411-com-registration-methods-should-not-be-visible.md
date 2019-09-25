---
title: 'CA1411: Metody registrace modelu COM by neměly být viditelné'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e9582fb6bbdbda8aefbb60e2c69d16380eec3dff
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234747"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: Metody registrace modelu COM by neměly být viditelné

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|Kategorie|Microsoft. interoperabilita|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Metoda, která je označena <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atributem nebo, je externě viditelná.

## <a name="rule-description"></a>Popis pravidla
Pokud je sestavení registrováno pomocí modelu COM (Component Object Model), položky jsou přidány do registru pro každý typ viditelný v sestavení. Metody, které jsou označeny <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> atributem a <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> , jsou volány během procesu registrace a zrušení registrace, v uvedeném pořadí, ke spuštění uživatelského kódu, který je specifický pro registraci nebo zrušení registrace těchto typů. Tento kód by neměl být volán mimo tyto procesy.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, změňte přístupnost metody `private` na nebo `internal` (`Friend` v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
Následující příklad ukazuje dvě metody, které porušují pravidlo.

[!code-csharp[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
[!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]

## <a name="related-rules"></a>Související pravidla
[CA1410: Metody registrace modelu COM by se měly shodovat](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [Registrování sestav pomocí modelu COM](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (nástroj registrace sestavení)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)