---
title: 'CA1052: Statické typy držitelů by měly být statické nebo NotInheritable.'
ms.date: 07/25/2019
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 757b6b46e0c0892f5eb4c868b15654b29cd51c0e
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235620"
---
# <a name="ca1052-static-holder-types-should-be-static-or-notinheritable"></a>CA1052: Statické typy držitelů by měly být statické nebo NotInheritable.

|||
|-|-|
|TypeName|StaticHolderTypesAnalyzer|
|CheckId|CA1052|
|Kategorie|Microsoft.Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Neabstraktní typ obsahuje pouze statické členy (kromě možného výchozího konstruktoru) a není deklarován se [statickým](/dotnet/csharp/language-reference/keywords/static) nebo [sdíleným](/dotnet/visual-basic/language-reference/modifiers/shared) modifikátorem.

Ve výchozím nastavení toto pravidlo vyhledává pouze externě viditelné typy, ale je možné jej [nakonfigurovat](#configurability).

## <a name="rule-description"></a>Popis pravidla

Pravidlo CA1052 předpokládá, že typ, který obsahuje pouze statické členy, není navržen tak, aby byl zděděn, protože typ neposkytuje žádné funkce, které mohou být přepsány v odvozeném typu. Typ, který není určen k dědění, by měl být označen `static` modifikátorem v C# , aby bylo možné jeho použití jako základní typ zakázat. Kromě toho by měl být odebrán jeho výchozí konstruktor. V Visual Basic musí být třída převedena na [modul](/dotnet/visual-basic/language-reference/statements/module-statement).

Toto pravidlo se neaktivuje u abstraktních tříd nebo tříd, které mají základní třídu. Pravidlo však aktivuje třídy, které podporují prázdné rozhraní.

> [!NOTE]
> V rámci implementace FxCop Analyzer tohoto pravidla zahrnuje i funkci [pravidla CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md).

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, označte typ jako `static` a odeberte výchozí konstruktor (C#) nebo jej převeďte na modul (Visual Basic).

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Potlačí upozornění z tohoto pravidla pouze v případě, že je typ navržen tak, aby byl zděděn. Absence `static` modifikátoru naznačuje, že typ je užitečný jako základní typ.

## <a name="configurability"></a>Konfigurovatelnost

Pokud toto pravidlo spouštíte z [analyzátorů FxCop](install-fxcop-analyzers.md) (a ne pomocí starší verze analýzy), můžete nakonfigurovat, které části základu kódu mají spustit toto pravidlo, na základě jejich přístupnosti. Například chcete-li určit, že pravidlo by mělo běžet pouze proti neveřejnému povrchu rozhraní API, přidejte do souboru EditorConfig v projektu následující dvojici klíč-hodnota:

```ini
dotnet_code_quality.ca1052.api_surface = private, internal
```

Tuto možnost můžete nakonfigurovat jenom pro toto pravidlo, pro všechna pravidla nebo pro všechna pravidla v této kategorii (návrh). Další informace najdete v tématu [Konfigurace analyzátorů FxCop](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Příklad porušení

Následující příklad ukazuje typ, který je v rozporu s pravidlem:

[!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
[!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
[!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]

## <a name="fix-with-the-static-modifier"></a>Oprava pomocí modifikátoru static

Následující příklad ukazuje, jak opravit porušení tohoto pravidla označením typu s `static` modifikátorem v: C#

```csharp
public static class StaticMembers
{
    public static int SomeProperty { get; set; }
    public static void SomeMethod() { }
}
```