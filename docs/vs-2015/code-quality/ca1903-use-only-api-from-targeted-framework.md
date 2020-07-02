---
title: 'CA1903: použijte pouze rozhraní API z cíleného rozhraní | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 10649b4106a280089fd6b086167c7e92bff1300b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545246"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903: Používejte jen rozhraní API z cílové architektury
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio najdete v tématu [CA1903: Používejte pouze rozhraní API z cíleného rozhraní](/visualstudio/code-quality/ca1903-use-only-api-from-targeted-framework).

|Položka|Hodnota|
|-|-|
|TypeName|UseOnlyApiFromTargetedFramework|
|CheckId|CA1903|
|Kategorie|Microsoft. přenositelnost|
|Narušující změna|Přerušení – při vyvolání proti podpisu externě viditelného člena nebo typu.<br /><br /> Bez přerušení – při vyvolání v těle metody.|

## <a name="cause"></a>Příčina
 Člen nebo typ používá člen nebo typ, který byl představen v aktualizaci Service Pack, která nebyla zahrnuta do cíleného rozhraní projektu.

## <a name="rule-description"></a>Popis pravidla
 Nové členy a typy byly součástí .NET Framework 2,0 Service Pack 1 a 2, .NET Framework 3,0 Service Pack 1 a 2 a .NET Framework 3,5 Service Pack 1. Projekty, které cílí na hlavní verze .NET Framework, můžou neúmyslně převzít závislosti na těchto nových rozhraních API. Chcete-li zabránit této závislosti, toto pravidlo je vyvoláno při použití všech nových členů a typů, které nebyly zahrnuty ve výchozím nastavení s cílovým rozhraním projektu.

 **Závislosti cílové architektury a aktualizace Service Pack**

|Položka|Hodnota|
|-|-|
|Když je cílová architektura|Aktivuje se při použití členů představených v.|
|.NET Framework 2,0|.NET Framework 2,0 SP1, .NET Framework 2,0 SP2|
|.NET Framework 3.0|.NET Framework 2,0 SP1, .NET Framework 2,0 SP2, .NET Framework 3,0 SP1, .NET Framework 3,0 SP2|
|.NET Framework 3.5|.NET Framework 3.5 SP1|
|.NET Framework 4|–|

 Chcete-li změnit cílové rozhraní .NET Framework projektu, přečtěte si téma [cílení na konkrétní verzi .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li odebrat závislost na aktualizaci Service Pack, odeberte všechna použití nového člena nebo typu. Pokud se jedná o záměrné závislosti, potlačit upozornění nebo vypnout toto pravidlo.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit upozornění z tohoto pravidla, pokud se nejedná o záměrné závislosti na zadané aktualizaci Service Pack. V takovém případě se aplikace nemusí podařit spustit v systémech bez nainstalované této aktualizace Service Pack. Potlačit upozornění nebo vypnout toto pravidlo, pokud se jednalo o záměrné závislosti.

## <a name="example"></a>Příklad
 Následující příklad ukazuje třídu, která používá typ DateTimeOffset, který je k dispozici pouze v rozhraní .NET 2,0 Service Pack 1. Tento příklad vyžaduje, aby byl v rozevíracím seznamu cílové rozhraní ve vlastnostech projektu vybráno .NET Framework 2,0.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework.cs#1)]

## <a name="example"></a>Příklad
 Následující příklad opravuje dříve popsané porušení nahrazením využití typu DateTimeOffset typem DateTime.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework2/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework2.cs#1)]

## <a name="see-also"></a>Viz také
 [Upozornění na přenositelnost](../code-quality/portability-warnings.md) [cílící na konkrétní verzi .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)
