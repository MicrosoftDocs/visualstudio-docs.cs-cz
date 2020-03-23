---
title: 'DA0001: Použití StringBuilder pro zřetězení | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0001
- vs.performance.rules.DAUseStringBuilder
- vs.performance.1
- vs.performance.rules.DA0001
ms.assetid: a7cc7613-ad5f-48c8-bd2b-56372cc12dfc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0d93de6ce901bfe4d72628f778b18420beb5ebee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779503"
---
# <a name="da0001-use-stringbuilder-for-concatenations"></a>DA0001: Pro zřetězování používejte StringBuilder

|||
|-|-|
|Id pravidla|DA0001 řekl:|
|Kategorie|Použití rozhraní .NET Framework|
|Metody profilování|Vzorkování<br /><br /> Instrumentace|
|Zpráva|Zvažte použití StringBuilder pro zřetězení řetězců|
|Typ zprávy|Upozornění|

## <a name="cause"></a>Příčina
 Volání System.String.Concat jsou významnou část dat profilování. Zvažte <xref:System.Text.StringBuilder> použití třídy k vytvoření řetězců z více segmentů.

## <a name="rule-description"></a>Popis pravidla
 Objekt <xref:System.String> je neměnný. Proto všechny změny řetězce vytvoří nový objekt řetězce a uvolnění paměti původní. Toto chování je stejné, zda voláte String.Concat explicitně nebo použijte operátory zřetězení řetězce jako + nebo +=.. Výkon programu může snížit, pokud jsou tyto metody často volány, například když jsou znaky přidány do řetězce v těsné smyčce.

 Třída StringBuilder je proměnlivý objekt a na rozdíl od System.String, většina metod na StringBuilder, které upravují instanci této třídy vrátit odkaz na stejnou instanci. Můžete vložit znaky nebo připojit text k instanci StringBuilder a odebrat nebo nahradit znaky v instanci bez nutnosti přidělení nové instance a odstranění původní instance.

## <a name="how-to-investigate-a-warning"></a>Jak prošetřit varování
 Poklepáním na zprávu v okně **Seznam chyb** přejděte do [zobrazení podrobností funkce](../profiling/function-details-view.md) dat profilů vzorkování. Najděte části programu, které nejčastěji používají zřetězení řetězců. Třídu StringBuilder použijte pro složité manipulace s řetězci, včetně operací častého zřetězení řetězců.

 Další informace o tom, jak pracovat s řetězci, [části Operace řetězce](/previous-versions/msp-n-p/ff647790(v=pandp.10)#string-operations) kapitoly 5 – Zlepšení výkonu [spravovaného kódu](/previous-versions/msp-n-p/ff647790(v=pandp.10)) v knihovně Microsoft Patterns and Practices.
