---
title: 'CA2102: zachytávání výjimek mimo CLSCompliant v obecných obslužných rutinách | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e2335b6d2bc3a5e99f0e6de1afefac4f42de0501
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521300"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: Zachycujte výjimky bez CLSCompliant v obecných obslužných rutinách
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|Kategorie|Microsoft.Security|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Člen v sestavení, které není označeno <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> nebo je označen jako, `RuntimeCompatibility(WrapNonExceptionThrows = false)` obsahuje blok catch, který zpracovává <xref:System.Exception?displayProperty=fullName> a neobsahuje okamžitě následující obecný blok catch. Toto pravidlo ignoruje [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] sestavení.

## <a name="rule-description"></a>Popis pravidla
 Blok catch, který zpracovává <xref:System.Exception> všechny výjimky kompatibilní se specifikací CLS (Common Language Specification). Nevyhovuje však výjimkám, které nejsou kompatibilní se specifikací CLS. Výjimky, které nejsou kompatibilní se specifikací CLS, mohou být vyvolány z nativního kódu nebo ze spravovaného kódu vygenerovaného assemblerem jazyka MSIL (Microsoft Intermediate Language). Všimněte si, že C# a [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kompilátory neumožňují vyvolání výjimek nevyhovujících specifikaci CLS a [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] nezachytí výjimky nekompatibilní se specifikací CLS. Pokud záměr bloku catch má zpracovat všechny výjimky, použijte následující obecný syntax bloku catch.

- Jazyk`catch {}`

- C++: `catch(...) {}` nebo`catch(Object^) {}`

  Neošetřená výjimka, která není kompatibilní se specifikací CLS, se stala problémem se zabezpečením v případě, že byla dříve povolená oprávnění odebrána v bloku catch. Vzhledem k tomu, že výjimky nekompatibilní se specifikací CLS nejsou zachyceny, by škodlivá metoda, která vyvolá výjimku nekompatibilní se specifikací CLS, mohla běžet se zvýšenými oprávněními.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, je-li záměr zachytit všechny výjimky, nahraďte nebo přidejte obecný blok catch nebo označte sestavení `RuntimeCompatibility(WrapNonExceptionThrows = true)` . Pokud jsou v bloku catch odebrána oprávnění, duplikujte funkci v obecném bloku catch. Pokud není záměrem zpracovat všechny výjimky, nahraďte blok catch, který zpracovává <xref:System.Exception> bloky catch, které zpracovávají konkrétní typy výjimek.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 V případě, že blok try neobsahuje žádné příkazy, které by mohly vygenerovat výjimku nekompatibilní se specifikací CLS, je bezpečné potlačit upozornění od tohoto pravidla. Protože jakýkoliv nativní nebo spravovaný kód může vyvolat výjimku nekompatibilní se specifikací CLS, vyžaduje se znalost veškerého kódu, který lze spustit ve všech cestách kódu uvnitř bloku try. Všimněte si, že modul CLR nevolá výjimky, které nejsou kompatibilní se specifikací CLS.

## <a name="example"></a>Příklad
 Následující příklad ukazuje třídu jazyka MSIL, která vyvolá výjimku, která není kompatibilní se specifikací CLS.

```
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

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, která obsahuje obecný blok catch, který splňuje pravidlo.

 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.CatchNonClsCompliantException/cs/FxCop.Security.CatchNonClsCompliantException.cs#1)]

 Následujícím způsobem zkompilujte předchozí příklady.

```
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>Související pravidla
 [CA1031: Nezachycujte výjimky obecného typu](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>Viz také
 [Výjimky a zpracování výjimek](https://msdn.microsoft.com/library/0001887f-4fa2-47e2-8034-2819477e2344) [Ilasm.exe (IL Assembler)](https://msdn.microsoft.com/library/4ca3a4f0-4400-47ce-8936-8e219961c76f) [Přepisuje kontrolu zabezpečení](https://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28) [nezávislá na jazyku a jazykově nezávislé komponenty](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6) .
