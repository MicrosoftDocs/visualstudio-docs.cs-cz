---
title: 'CA1903: Používejte jen rozhraní API z cílové architektury'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 704972127130cc7be991213249ff41212fa40676
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233272"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903: Používejte jen rozhraní API z cílové architektury

|||
|-|-|
|TypeName|UseOnlyApiFromTargetedFramework|
|CheckId|CA1903|
|Kategorie|Microsoft. přenositelnost|
|Zásadní změna|Přerušení – při vyvolání proti podpisu externě viditelného člena nebo typu.<br /><br /> Bez přerušení – při vyvolání v těle metody.|

## <a name="cause"></a>příčina
Člen nebo typ používá člen nebo typ, který byl představen v aktualizaci Service Pack, která nebyla zahrnuta do cíleného rozhraní projektu.

## <a name="rule-description"></a>Popis pravidla
Nové členy a typy byly součástí .NET Framework 2,0 Service Pack 1 a 2, .NET Framework 3,0 Service Pack 1 a 2 a .NET Framework 3,5 Service Pack 1. Projekty, které cílí na hlavní verze .NET Framework, můžou neúmyslně převzít závislosti na těchto nových rozhraních API. Chcete-li zabránit této závislosti, toto pravidlo je vyvoláno při použití všech nových členů a typů, které nebyly zahrnuty ve výchozím nastavení s cílovým rozhraním projektu.

**Závislosti cílové architektury a aktualizace Service Pack**

|||
|-|-|
|Když je cílová architektura|Aktivuje se při použití členů představených v.|
|.NET Framework 2.0|.NET Framework 2,0 SP1, .NET Framework 2,0 SP2|
|.NET Framework 3.0|.NET Framework 2,0 SP1, .NET Framework 2,0 SP2, .NET Framework 3,0 SP1, .NET Framework 3,0 SP2|
|.NET Framework 3.5|.NET Framework 3.5 SP1|
|.NET Framework 4|Není k dispozici|

Chcete-li změnit cílové rozhraní .NET Framework projektu [, přečtěte si téma How to: Cílí na verzi .NET](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li odebrat závislost na aktualizaci Service Pack, odeberte všechna použití nového člena nebo typu. Pokud se jedná o záměrné závislosti, potlačit upozornění nebo vypnout toto pravidlo.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Potlačit upozornění z tohoto pravidla, pokud se nejedná o záměrné závislosti na zadané aktualizaci Service Pack. V takovém případě se aplikace nemusí podařit spustit v systémech bez nainstalované této aktualizace Service Pack. Potlačit upozornění nebo vypnout toto pravidlo, pokud se jednalo o záměrné závislosti.

## <a name="example"></a>Příklad
Následující příklad ukazuje třídu, která používá typ DateTimeOffset, který je k dispozici pouze v rozhraní .NET 2,0 Service Pack 1. Tento příklad vyžaduje, aby byl v rozevíracím seznamu cílové rozhraní ve vlastnostech projektu vybráno .NET Framework 2,0.

[!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]

## <a name="example"></a>Příklad
Následující příklad opravuje dříve popsané porušení nahrazením využití typu DateTimeOffset typem DateTime.

[!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]

## <a name="see-also"></a>Viz také:

- [Upozornění přenositelnosti](../code-quality/portability-warnings.md)
- [Přehled cílení na rozhraní](../ide/visual-studio-multi-targeting-overview.md)