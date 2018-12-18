---
title: 'CA2102: Zachycujte výjimky bez CLSCompliant v obecné obslužné rutině'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f5af37daba4ce1791c5485d65734d1dd8c3d87f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887043"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: Zachycujte výjimky bez CLSCompliant v obecné obslužné rutině

|||
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|Kategorie|Microsoft.Security|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina

Člen v sestavení, který není označen atributem <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> nebo je označeno `RuntimeCompatibility(WrapNonExceptionThrows = false)` obsahuje zachytávací blok, který zpracovává <xref:System.Exception?displayProperty=fullName> a neobsahuje bezprostředně následující obecný zachytávací blok. Toto pravidlo ignoruje [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] sestavení.

## <a name="rule-description"></a>Popis pravidla

Blok catch, který zpracovává <xref:System.Exception> zachytává všechny výjimky kompatibilní s specifikace CLS (Common Language). To však nebude zachytávat výjimky kompatibilní neodpovídající specifikaci CLS. Specifikací CLS kompatibilní výjimky mohou být vyvolány z nativního kódu nebo ze spravovaného kódu, který vygeneroval Microsoft zprostředkující jazyk MSIL Assembler. Všimněte si, že jazyka C# a [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kompilátory neumožňují neodpovídající specifikaci CLS kompatibilní výjimky, která je vyvolána a [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nezachytí výjimky kompatibilní neodpovídající specifikaci CLS. Pokud je cílem bloku catch ošetření všech výjimek, použijte následující syntaxi obecný zachytávací blok.

- C#: `catch {}`

- Jazyk C++: `catch(...) {}` nebo `catch(Object^) {}`

Kompatibilní výjimka neošetřená neodpovídající specifikaci CLS nebude potíže se zabezpečením, když se odeberou dřív povolené oprávnění v bloku catch. Protože nejsou zachyceny kompatibilní výjimky neodpovídající specifikaci CLS, může se zvýšenými oprávněními spustit škodlivý metodu, která se vyvolá výjimka specifikací CLS.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

Chcete-li opravit porušení tohoto pravidla, pokud je cílem zachytit všechny výjimky, nahradit nebo přidat obecný zachytávací blok nebo označit sestavení `RuntimeCompatibility(WrapNonExceptionThrows = true)`. Pokud jsou oprávnění odebrána v bloku catch, duplicitní funkce v obecné blok catch. Pokud není cílem ošetření všech výjimek, nahraďte blok catch, který zpracovává <xref:System.Exception> s bloky catch, které zpracovávají výjimky pro konkrétní typy.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Je bezpečné potlačit upozornění tohoto pravidla, je-li testovaného bloku neobsahuje žádné příkazy, které mohou vytvořit kompatibilní výjimka kompilace neodpovídající specifikaci CLS. Vzhledem k tomu, že žádný nativní nebo spravovaný kód může vyvolat bez specifikace CLS výjimka, to se vyžaduje znalost veškerý kód, který mohou být provedeny ve všech cestách kódu uvnitř bloku try. Všimněte si, že nejsou vyvolány kompatibilní výjimky neodpovídající specifikaci CLS modulem common language runtime.

## <a name="example-1"></a>Příklad 1

Následující příklad ukazuje třídu jazyk MSIL, která vyvolá kompatibilní výjimka kompilace neodpovídající specifikaci CLS.

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

Následující příklad ukazuje metodu, která obsahuje obecný zachytávací blok, který splňuje pravidlo.

[!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]

V předchozích příkladech kompilaci následujícím způsobem.

```cpp
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>Související pravidla

[CA1031: Nezachycujte výjimky obecného typu](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>Viz také:

- [Výjimky a jejich zpracování](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)
- [Ilasm.exe (IL Assembler)](/dotnet/framework/tools/ilasm-exe-il-assembler)
- [Jazyková nezávislost a jazykově nezávislé komponenty](/dotnet/standard/language-independence-and-language-independent-components)