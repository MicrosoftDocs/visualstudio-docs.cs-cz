---
title: 'DA0012: významné množství reflexe | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAReflection
- vs.performance.12
- vs.performance.rules.DA0012
- vs.performance.DA0011
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54626c07fb8d15f585e800f03911dd465395d795
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850250"
---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012: Vysoký objem odrazů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ID pravidla | DA0012 |  
| Kategorie |. Použití rozhraní .NET Framework |  
| Metody profilování | Vzorkování |  
| Zpráva | Je možné, že reflexe vyřadí nadměrné využití. Jedná se o náročnou operaci. |  
| Typ pravidla | Upozornění |  
  
## <a name="cause"></a>příčina  
 Volání metod System. Reflection, jako jsou metodu InvokeMember a GetMember nebo na metody typu, jako je MemberInvoke, jsou významným podílem dat profilování. Pokud je to možné, zvažte nahrazení těchto metod pomocí počáteční vazby na metody závislých sestavení.  
  
## <a name="rule-description"></a>Popis pravidla  
 Reflexe je flexibilním zařízením .NET Framework, které lze použít k provedení pozdní vazby vaší aplikace k závislému sestavení run-time nebo k vytvoření a dynamickému spouštění nových typů za běhu. Nicméně tyto techniky mohou snížit výkon, pokud jsou používány často nebo se nazývají v těsných smyčkách.  
  
 Další informace najdete v části [reflexe a pozdní vazby](https://msdn.microsoft.com/library/ms998547.aspx#scalenetchapt05_topic31) kapitoly 5 – zlepšení výkonu spravovaného kódu v tématu zlepšení výkonu a škálovatelnosti aplikace .NET v knihovně Microsoft Patterns and Practices Library na webu MSDN.  
  
## <a name="how-to-investigate-a-warning"></a>Jak prozkoumat upozornění  
 Dvakrát klikněte na zprávu v okně Seznam chyb a přejděte k [zobrazení podrobností o funkci](../profiling/function-details-view.md) dat profilace. Zkontrolujte funkce volání metody System. Type nebo System. Reflection, abyste našli oddíly programu, které usnadňují použití rozhraní API pro reflexi rozhraní .NET. Vyhněte se použití metod, které vracejí metadata. Pokud je výkon vaší aplikace kritický, může být nutné vyhnout se použití pozdní vazby a vytváření typů dynamicky za běhu.
