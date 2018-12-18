---
title: 'CA1903: Použijte pouze API z cíleného rozhraní | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1c23b25029775cd3abca84e695c50b5a0fdf68cf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49191568"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903: Použijte pouze API z cílového rozhraní .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio 2017, najdete v části [CA1903: použijte pouze API z cíleného rozhraní](https://docs.microsoft.com/visualstudio/code-quality/ca1903-use-only-api-from-targeted-framework) na webu docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|UseOnlyApiFromTargetedFramework|  
|CheckId|CA1903|  
|Kategorie|Microsoft.Portability|  
|Narušující změna|Zásadní - při vyvolání s podpisem externě viditelného členu nebo typu.<br /><br /> Pevné - při vyvolání v těle metody.|  
  
## <a name="cause"></a>příčina  
 Člen nebo typ používá člen nebo typ, který byl zaveden v aktualizaci service pack, která není součástí cílové rozhraní projektu.  
  
## <a name="rule-description"></a>Popis pravidla  
 Nové členy a typy byly součástí rozhraní .NET Framework 2.0 Service Pack 1 a 2, rozhraní .NET Framework 3.0 Service Pack 1 a 2 a rozhraní .NET Framework 3.5 Service Pack 1. Projekty, které cílí hlavní verze rozhraní .NET Framework neúmyslně může trvat závislosti na těchto nových rozhraní API. Pokud chcete zabránit této závislosti, toto pravidlo je vyvoláno na použití nové členy a typy, které nejsou zahrnuty ve výchozím nastavení se cílové rozhraní projektu.  
  
 **Cílová architektura a závislosti Service Pack**  
  
|||  
|-|-|  
|Pokud je Cílová architektura|Je aktivována na použití členy zavedený|  
|.NET Framework 2.0|Rozhraní .NET framework 2.0 SP1, .NET Framework 2.0 SP2|  
|.NET Framework 3.0|Rozhraní .NET framework 2.0 SP1, .NET Framework 2.0 SP2, rozhraní .NET Framework 3.0 s aktualizací SP1, .NET Framework 3.0 s aktualizací SP2|  
|.NET Framework 3.5|.NET Framework 3.5 SP1|  
|.NET Framework 4|Není k dispozici|  
  
 Chcete-li změnit cílový rámec projektu, [cílení na konkrétní verzi rozhraní .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
## <a name="how-to-fix-violations"></a>Jak vyřešit porušení  
 K odebírání závislostí pro aktualizace service pack, odeberte všechny použití nového člena nebo typu. Pokud je to rozhodnout vědomě a záměrně závislost, potlačit upozornění nebo vypnout toto pravidlo.  
  
## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění  
 Nepotlačujte upozornění tohoto pravidla, pokud to není záměrné závislost na balíčku zadaná služba. V takovém případě se vaše aplikace nemusí podařit spustit v systémech bez této aktualizace service pack nainstalována. Potlačit upozornění nebo vypněte toto pravidlo, pokud jste to byli rozhodnout vědomě a záměrně závislost.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje třídu, která používá typ DateTimeOffset, která je dostupná pouze v rozhraní .NET 2.0 Service Pack 1. Tento příklad vyžaduje, aby byla vybrána rozhraní .NET Framework 2.0 v rozevíracím seznamu cílovou architekturu ve vlastnostech projektu.  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework.cs#1)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu řeší dříve popsaná porušení nahrazením použití typu DateTimeOffset typu DateTime.  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework2/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework2.cs#1)]  
  
## <a name="see-also"></a>Viz také  
 [Upozornění přenositelnosti](../code-quality/portability-warnings.md)   
 [Cílení na konkrétní verzi rozhraní .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)

