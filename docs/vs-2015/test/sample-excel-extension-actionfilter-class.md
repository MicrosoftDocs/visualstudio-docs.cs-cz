---
title: 'Ukázka rozšíření aplikace Excel: třída ActionFilter | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4c286f25159f3ee1934a27d2242e97482f7ec424
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672186"
---
# <a name="sample-excel-extension-actionfilter-class"></a>Ukázka rozšíření aplikace Excel: třída ActionFilter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato interní třída rozšiřuje třídu [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)) a představuje filtr pro testovací akce u prvku [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].

## <a name="simple-properties"></a>Jednoduché vlastnosti
 Tyto vlastnosti jen pro čtení umožňují vývojářům určit, jak má být tento filtr akcí testů proveden pomocí rozhraní programového testování uživatelského rozhraní. Například vlastnost `UITestActionFilter.Name` poskytuje název filtru akcí. Další vlastnosti získají `UITestActionFilter.Category` filtru akcí, `UITestActionFilter.FilterType`, název `UITestActionFilter.Group` pro testovací akce, které jsou filtrovány pomocí tohoto filtru akcí testu. Jiné označují, zda se má `UITestActionFilter.ApplyTimeout` a také zda `UITestActionFilter.Enabled` akce testu.

## <a name="processrule-method"></a>Metoda ProcessRule
 Tato metoda je volána rozhraním programového testování uživatelského rozhraní a spustí filtr proti poskytnuté `IUITestActionStack`. Toto konkrétní přepsání odebere akci myši na buňku, pokud další akce v zásobníku odesílá stisknutí kláves do buňky. Pak vrátí `false`.

## <a name="private-methods"></a>Soukromé metody
 Metoda `IsLeftClick` určuje, zda zadaná akce představuje kliknutí levým tlačítkem myši. Metoda `AreActionsOnSameExcelCell` určuje, zda jsou dvě zadané akce provedeny ve stejné buňce v aplikaci Excel.

## <a name="see-also"></a>Viz také:

- [Rozšiřování programových testů UI a záznamů akcí k podpoře Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
