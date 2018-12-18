---
title: 'Da0012: vysoký Objem odrazů | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAReflection
- vs.performance.12
- vs.performance.rules.DA0012
- vs.performance.DA0011
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 191edf9cc6a3dc9ff177b075e2967cb328afc9c5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893920"
---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012: Vysoký objem odrazů

|||  
|-|-|  
|Id pravidla|DA0012 VYSOKÝ|  
|Kategorie|Použití rozhraní .NET framework|  
|Metod profilace|Vzorkování|  
|Zpráva|Budete pravděpodobně používáte nadměrně reflexi. Je náročná operace.|  
|Typ pravidla|Upozornění|  

## <a name="cause"></a>příčina  
 Volání metody System.Reflection například metodu InvokeMember a GetMember nebo typ metody, jako je například MemberInvoke je podstatnou část dat profilování. Pokud je to možné, zvažte nahrazení tyto metody s časná vazba metod závislá sestavení.  

## <a name="rule-description"></a>Popis pravidla  
 Reflexe je flexibilní rozhraní .NET Framework, který slouží k provádění pozdní vazba vaší aplikace na závislé sestavení za běhu nebo k vytvoření a dynamicky za běhu spusťte nové typy zařízení. Tyto postupy však může snížit výkon, pokud jsou často používané nebo volat v těsné smyčky.  

 Další informace najdete v tématu [reflexe a pozdní vazby](http://go.microsoft.com/fwlink/?LinkId=177826) část kapitola 5 – vylepšení spravovaných výkon kódu objemu zlepšení výkonu aplikace .NET a škálovatelnosti Microsoft Patterns and Practices Knihovna na webové stránce MSDN.  

## <a name="how-to-investigate-a-warning"></a>Zkoumání upozornění  
 Dvakrát klikněte na zprávu v okně Seznam chyb, přejděte [zobrazení podrobností funkce](../profiling/function-details-view.md) dat profilování. Zkontrolujte volání funkce System.Type nebo System.Reflection metody, která najdete v částech programu, které nejčastěji použití rozhraní API reflexe .NET. Vyhněte se použití metod, které vracejí metadata. Když je nejdůležitější výkon vaší aplikace, můžete potřebovat nepoužívejte pozdní vazby a dynamické vytváření typů v době běhu.