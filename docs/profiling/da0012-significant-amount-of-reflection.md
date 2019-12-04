---
title: 'DA0012: významné množství reflexe | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAReflection
- vs.performance.12
- vs.performance.rules.DA0012
- vs.performance.DA0011
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1c1b96e9a73b488ba9c9920e8ea43e27f78f67ed
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777670"
---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012: Vysoký objem odrazů

|||
|-|-|
|Id pravidla|DA0012|
|Kategorie|Využití .NET Framework|
|Metody profilace|Kontrol|
|Zpráva|Je možné, že reflexe vyřadí nadměrné využití. Tato operace je náročná.|
|Typ pravidla|Upozornění|

## <a name="cause"></a>příčina
 Volání metod System. Reflection, jako jsou metodu InvokeMember a GetMember nebo na metody typu, jako je MemberInvoke, jsou významným podílem dat profilování. Pokud je to možné, zvažte nahrazení těchto metod pomocí počáteční vazby na metody závislých sestavení.

## <a name="rule-description"></a>Popis pravidla
 Reflexe je flexibilním zařízením .NET Framework, které lze použít k provedení pozdní vazby vaší aplikace k závislému sestavení run-time nebo k vytvoření a dynamickému spouštění nových typů za běhu. Nicméně tyto techniky mohou snížit výkon, pokud jsou používány často nebo se nazývají v těsných smyčkách.

 Další informace najdete v části [reflexe a pozdní vazby](/previous-versions/msp-n-p/ff647790(v=pandp.10)#reflection-and-late-binding) kapitoly 5 – zlepšení výkonu spravovaného kódu v tématu zlepšení výkonu a škálovatelnosti aplikace .NET v knihovně Microsoft Patterns and Practices Library na webu MSDN.

## <a name="how-to-investigate-a-warning"></a>Jak prozkoumat upozornění
 Dvakrát klikněte na zprávu v okně Seznam chyb a přejděte k [zobrazení podrobností o funkci](../profiling/function-details-view.md) dat profilace. Zkontrolujte funkce volání metody System. Type nebo System. Reflection, abyste našli oddíly programu, které usnadňují použití rozhraní API pro reflexi rozhraní .NET. Vyhněte se použití metod, které vracejí metadata. Pokud je výkon vaší aplikace kritický, může být nutné vyhnout se použití pozdní vazby a vytváření typů dynamicky za běhu.
