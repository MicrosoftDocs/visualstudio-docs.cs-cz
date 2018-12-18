---
title: 'CA1411: Metody registrace modelu COM by neměly být viditelné'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0cd599ee67182084e7f2fb663d343281b0a8b079
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551704"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: Metody registrace modelu COM by neměly být viditelné

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|Kategorie|Microsoft.Interoperability|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina

Metoda, která je označena <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> nebo <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atribut je externě viditelná.

## <a name="rule-description"></a>Popis pravidla
 Když sestavení registrováno s modelu COM (Component Object), položky se přidají do registru pro každý typ viditelný modulem COM v sestavení. Metody, které jsou označené <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> a <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> atributy jsou volány během procesu registrace a zrušení registrace, ke spuštění uživatelský kód, který je specifický pro registraci nebo zrušení registrace z těchto typů. Tento kód by neměla být volána mimo tyto procesy.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte přístupnost metody, která `private` nebo `internal` (`Friend` v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje dvě metody, které se pravidlo porušují.

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]

## <a name="related-rules"></a>Související pravidla
 [CA1410: Metody registrace modelu COM by si měly odpovídat](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [Registrování sestav pomocí modelu COM](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (nástroj registrace sestavení)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)