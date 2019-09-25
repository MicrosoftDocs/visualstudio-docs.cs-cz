---
title: 'CA1410: Metody registrace modelu COM by si měly odpovídat'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bca9e06c861ab2bcaceead8bf8ee195b64e45c83
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234739"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: Metody registrace modelu COM by si měly odpovídat

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|Kategorie|Microsoft. interoperabilita|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Typ deklaruje metodu, která je označena <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> atributem, ale nedeklaruje metodu, která je označena <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atributem, nebo naopak.

## <a name="rule-description"></a>Popis pravidla

Pro klienty modelu COM (Component Object Model) pro vytvoření typu .NET musí být tento typ nejprve zaregistrován. Je-li k dispozici, metoda, která je označena <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> atributem, je volána během procesu registrace pro spuštění kódu zadaného uživatelem. Odpovídající metoda, která je označena <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> atributem, je volána během procesu zrušení registrace pro vrácení operací registrační metody.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, přidejte odpovídající metodu registrace nebo zrušení registrace.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad

Následující příklad ukazuje typ, který je v rozporu s pravidlem. Kód s komentářem zobrazuje opravu porušení.

[!code-csharp[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
[!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]

## <a name="related-rules"></a>Související pravidla

[CA1411: Metody registrace modelu COM by neměly být viditelné](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [Registrace sestavení pomocí modelu COM](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (nástroj registrace sestavení)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)