---
title: 'DA0001: Pro zřetězování používejte StringBuilder | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0001
- vs.performance.rules.DAUseStringBuilder
- vs.performance.1
- vs.performance.rules.DA0001
ms.assetid: a7cc7613-ad5f-48c8-bd2b-56372cc12dfc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a71a31ec3caf08dd2a6f4b4e044b929dade11f0f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855869"
---
# <a name="da0001-use-stringbuilder-for-concatenations"></a>DA0001: Pro zřetězování používejte StringBuilder

|||  
|-|-|  
|Id pravidla|DA0001|  
|Kategorie|Použití rozhraní .NET framework|  
|Metod profilace|Vzorkování<br /><br /> Instrumentace|  
|Zpráva|Zvažte možnost použít StringBuilder pro zřetězení řetězců|  
|Typ zprávy|Upozornění|  

## <a name="cause"></a>příčina  
 Volání System.String.Concat jsou podstatnou část dat profilování. Zvažte použití <xref:System.Text.StringBuilder> třídy k vytvoření řetězce z více segmentů.  

## <a name="rule-description"></a>Popis pravidla  
 A <xref:System.String> objektu je neměnný. Proto všechny změny na řetězec vytvoří nový objekt řetězce a uvolnění paměti původní. Toto chování je stejný, ať můžete explicitně volat String.Concat nebo operátory zřetězení řetězců například + nebo +=... Pokud se může snížit výkon programu tyto metody jsou často volány, jako je například při přidávání znaků do řetězce v těsné smyčce.  

 Třída StringBuilder je měnitelný objekt a na rozdíl od System.String, většina metod, které upravují instance této třídy na StringBuilder vrátí odkaz na stejné instanci. Můžete vložit znaky nebo připojit k instanci StringBuilder text a odeberte nebo nahraďte znaků v instanci aplikace bez nutnosti přidělení nové instance a odstraníte původní instanci.  

## <a name="how-to-investigate-a-warning"></a>Zkoumání upozornění  
 Dvakrát klikněte na tuto zprávu najdete v **seznam chyb** okno a přejděte [zobrazení podrobností funkce](../profiling/function-details-view.md) odběru vzorků data profilu. Najdete v částech programu, které se používají nejvíce často zřetězení řetězců. Pomocí třídy StringBuilder pro manipulace s řetězci komplexní, včetně operace sřetězení časté řetězec.  

 Další informace o tom, jak pracovat s řetězci [operace s řetězci](http://go.microsoft.com/fwlink/?LinkId=177816) část [kapitola 5 - zlepšení výkonu kódu spravované](http://go.microsoft.com/fwlink/?LinkId=177817) v knihovně Microsoft Patterns and Practices.