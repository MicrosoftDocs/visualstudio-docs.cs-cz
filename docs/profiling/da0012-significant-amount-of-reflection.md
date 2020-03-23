---
title: 'DA0012: Značné množství reflexe | Dokumenty společnosti Microsoft'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777670"
---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012: Vysoký objem odrazů

|||
|-|-|
|Id pravidla|DA0012 řekl:|
|Kategorie|Použití rozhraní .NET Framework|
|Metody profilování|Vzorkování|
|Zpráva|Je možné, že používáte reflexe nadměrně. Je to drahá operace.|
|Typ pravidla|Upozornění|

## <a name="cause"></a>Příčina
 Volání System.Reflection metody jako InvokeMember a GetMember nebo Type metody jako MemberInvoke jsou významnou část dat profilování. Pokud je to možné, zvažte nahrazení těchto metod časnou vazbou na metody závislých sestavení.

## <a name="rule-description"></a>Popis pravidla
 Reflexe je flexibilní zařízení rozhraní .NET Framework, které lze použít k provedení pozdní vazby vaší aplikace na závislé sestavení za běhu nebo k vytvoření a dynamickému spuštění nových typů za běhu. Tyto techniky však může snížit výkon, pokud jsou používány často nebo volat v těsné smyčky.

 Další informace naleznete v části [Reflexe a pozdní vazba](/previous-versions/msp-n-p/ff647790(v=pandp.10)#reflection-and-late-binding) kapitoly 5 – Zlepšení výkonu spravovaného kódu ve zlepšení výkonu aplikací .NET a škálovatelnosti knihovny Microsoft Patterns and Practices v knihovně MSDN.

## <a name="how-to-investigate-a-warning"></a>Jak prošetřit varování
 Poklepáním na zprávu v okně Seznam chyb přejděte do [zobrazení podrobností o funkci](../profiling/function-details-view.md) dat profilování. Zkontrolujte volající funkce System.Type nebo System.Reflection metoda najít části programu, které nejčastěji používají rozhraní API .NET Reflection. Nepoužívejte metody, které vracejí metadata. Pokud je výkon vaší aplikace kritický, budete muset vyhnout použití pozdní vazby a vytváření typů dynamicky za běhu.
