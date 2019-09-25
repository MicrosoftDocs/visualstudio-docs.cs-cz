---
title: 'CA2102: Zachycujte výjimky bez CLSCompliant v obecných obslužných rutinách'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f62ad97bbb96f49a7263edd29f0f8a7c263bec4c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233015"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: Zachycujte výjimky bez CLSCompliant v obecných obslužných rutinách

|||
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|Kategorie|Microsoft.Security|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Člen v sestavení, které není označeno <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> nebo je označen `RuntimeCompatibility(WrapNonExceptionThrows = false)` jako, obsahuje blok catch, který zpracovává <xref:System.Exception?displayProperty=fullName> a neobsahuje okamžitě následující obecný blok catch. Toto pravidlo ignoruje [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] sestavení.

## <a name="rule-description"></a>Popis pravidla

Blok catch, který zpracovává <xref:System.Exception> všechny výjimky kompatibilní se specifikací CLS (Common Language Specification). Nevyhovuje však výjimkám, které nejsou kompatibilní se specifikací CLS. Výjimky, které nejsou kompatibilní se specifikací CLS, mohou být vyvolány z nativního kódu nebo ze spravovaného kódu vygenerovaného assemblerem jazyka MSIL (Microsoft Intermediate Language). Všimněte si, C# že [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kompilátory a neumožňují vyvolání výjimek nekompatibilních se specifikací CLS a [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nezachytí výjimky nekompatibilní se specifikací CLS. Pokud záměr bloku catch má zpracovat všechny výjimky, použijte následující obecný syntax bloku catch.

- C#: `catch {}`

- C++: `catch(...) {}` nebo`catch(Object^) {}`

Neošetřená výjimka, která není kompatibilní se specifikací CLS, se stala problémem se zabezpečením v případě, že byla dříve povolená oprávnění odebrána v bloku catch. Vzhledem k tomu, že výjimky nekompatibilní se specifikací CLS nejsou zachyceny, by škodlivá metoda, která vyvolá výjimku nekompatibilní se specifikací CLS, mohla běžet se zvýšenými oprávněními.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, je-li záměr zachytit všechny výjimky, nahraďte nebo přidejte obecný blok catch nebo označte sestavení `RuntimeCompatibility(WrapNonExceptionThrows = true)`. Pokud jsou v bloku catch odebrána oprávnění, duplikujte funkci v obecném bloku catch. Pokud není záměrem zpracovat všechny výjimky, nahraďte blok catch, který zpracovává <xref:System.Exception> bloky catch, které zpracovávají konkrétní typy výjimek.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

V případě, že blok try neobsahuje žádné příkazy, které by mohly vygenerovat výjimku nekompatibilní se specifikací CLS, je bezpečné potlačit upozornění od tohoto pravidla. Protože jakýkoliv nativní nebo spravovaný kód může vyvolat výjimku nekompatibilní se specifikací CLS, vyžaduje se znalost veškerého kódu, který lze spustit ve všech cestách kódu uvnitř bloku try. Všimněte si, že modul CLR nevolá výjimky, které nejsou kompatibilní se specifikací CLS.

## <a name="example-1"></a>Příklad 1

Následující příklad ukazuje třídu jazyka MSIL, která vyvolá výjimku, která není kompatibilní se specifikací CLS.

```cpp
.assembly ThrowNonClsCompliantException {}
.class public auto ansi beforefieldinit ThrowsExceptions
{
   .method public hidebysig static void
         ThrowNonClsException() cil managed
   {
      .maxstack  1
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()
      IL_0005:  throw
   }
}
```

## <a name="example-2"></a>Příklad 2

Následující příklad ukazuje metodu, která obsahuje obecný blok catch, který splňuje pravidlo.

[!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]

Následujícím způsobem zkompilujte předchozí příklady.

```cpp
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>Související pravidla

[CA1031: Nezachytit obecné typy výjimek](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>Viz také:

- [Výjimky a jejich zpracování](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)
- [Ilasm.exe (IL Assembler)](/dotnet/framework/tools/ilasm-exe-il-assembler)
- [Jazyková nezávislost a jazykově nezávislé komponenty](/dotnet/standard/language-independence-and-language-independent-components)