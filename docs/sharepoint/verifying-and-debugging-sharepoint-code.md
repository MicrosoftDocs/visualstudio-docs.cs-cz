---
title: Ověřování a ladění kódu služby SharePoint | Microsoft Docs
description: Ověřit a ladit kód služby SharePoint. Pomocí IntelliTrace můžete v řešení kontrolovat minulé události a aktuální stav. Testování částí použijte k tomu, abyste zajistili správné fungování vašich metod.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- unit testing [SharePoint development in Visual Studio]
- IntelliTrace [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, IntelliTrace
- SharePoint development in Visual Studio, unit testing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d406afbc0a8506262f1bdc17310802b7f41a931a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892135"
---
# <a name="verify-and-debug-sharepoint-code"></a>Ověření a ladění kódu pro SharePoint
Pomocí IntelliTrace a testování částí lze snadněji ladit řešení služby SharePoint a zajistit správnou funkčnost každé metody. Tyto funkce můžete použít pro projekty služby SharePoint v aplikaci Visual Studio podle stejných postupů jako u jiných typů projektů.

## <a name="intellitrace"></a>IntelliTrace
Pomocí IntelliTrace lze určit nejen aktuální stav řešení služby SharePoint, ale také událostí, ke kterým došlo v minulosti, a kontext, ve kterém k nim došlo. V řešení služby SharePoint lze přecházet zpět a vpřed do různých bodů, kdy byly zaznamenány události, a prohlížet stav a hodnoty proměnných v každém tomto bodě. Pomocí této dynamické navigace lze snadno a rychle ladit řešení služby SharePoint bez nutnosti nastavení mnoha zarážek. Můžete také uložit relaci ladění do souboru protokolu IntelliTrace (*. iTrace*), otevřít ho později v Visual Studio Enterprise a provést ladění po havárii. Soubor *. iTrace* obsahuje podrobné informace o tom, kdy a kde došlo k určitým chybám služby SharePoint, takže je možné snadněji zjistit, co způsobují chyby. Informace v souboru *. iTrace* jsou podmnožinou kompletního protokolu chyb, který vytváří jednotný systém protokolování (ULS) ve službě SharePoint. Tyto informace zahrnují události, které jsou specifické pro službu SharePoint, například kdy byl otevřen nebo zavřen profil uživatele a kdy byly načteny, přečteny nebo změněny vlastnosti projektu služby SharePoint. Je možné nastavit, které události IntelliTrace zaznamená. Další informace najdete v tématu [použití uložených IntelliTrace dat](../debugger/using-saved-intellitrace-data.md).

Dojde-li ve službě SharePoint k chybám, zobrazí dialogové okno identifikátor „ID korelace“ konkrétní chyby. ID korelace můžete také získat z událostí, které jsou uvedeny v souboru *. iTrace* . Chcete-li zobrazit seznam všech událostí, ke kterým došlo s daným ID korelace, můžete zadat ID v části **Analýza** stránky souhrnu IntelliTrace. V této části můžete zadat, zda chcete zobrazit pouze názvy událostí, ke kterým došlo, nebo názvy událostí a informace o jejich volání, dále název funkce, vstupní a výstupní body, parametry a návratové hodnoty.

Události sady Visual Studio můžete získat v IntelliTrace tak, že vyberete klávesu **F5** . Chcete-li získat události, které jsou specifické pro službu SharePoint, musíte shromáždit data IntelliTrace v rámci řešení služby SharePoint pomocí nástroje Microsoft Monitoring Agent. Tento nástroj shromažďuje data IntelliTrace a vytváří soubory *. iTrace* pro aplikace, které jsou nasazeny mimo sadu Visual Studio. Další informace najdete v tématu [funkce IntelliTrace](../debugger/intellitrace-features.md) a [Použití samostatného kolektoru IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).

## <a name="unit-test"></a>Test jednotek
Chyby lze v kódu snadněji vyhledat pomocí testování částí, ve kterých je kód psán a spouštěn v rámci testovacích metod. Tyto metody obsahují prázdné proměnné a kontrolní příkaz, který slouží k ověření logiky a funkčnosti projektu založeného na modelu objektu služby SharePoint. Další informace najdete v tématu [testování částí kódu](../test/unit-test-your-code.md).

### <a name="support-for-microsoft-fakes-framework"></a>Podpora rozhraní falešného od společnosti Microsoft
Projekty služby SharePoint podporují Microsoft Fakes, což je izolované rozhraní, ve kterém lze vytvářet zkušební kódy na základě delegátů a překryvných ovladačů v aplikacích, které jsou založeny na rozhraní .NET Framework. Pomocí rozhraní Fakes lze vytvářet, spravovat a zakládat fiktivní implementace v rámci testování součástí. Tyto kódy a překryvné ovladače izolují testování částí od prostředí. Zkušební kód lze vytvářet pro testování kódu, který spotřebovává rozhraní nebo nezapečetěné třídy skrze přepisovatelné metody. Překryvné ovladače lze vytvořit pro přesměrování zapečetěných tříd se statickými metodami nebo metodami, které nelze přepsat do alternativní překryvné implementace. Zkušební kód a překryvné ovladače lze také použít pro dynamické nastavení chování jednotlivých zkušebních členů. Další informace naleznete v [části izolování testovaného kódu s napodobeninami společnosti Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md).

## <a name="related-articles"></a>Související články

|Nadpis|Popis|
|-----------|-----------------|
|[IntelliTrace](../debugger/intellitrace.md)|Tento článek popisuje snadnější ladění řešení aplikace Visual Studio pomocí IntelliTrace.|
|[Návod: ladění aplikace služby SharePoint pomocí IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|Znázorňuje způsob vyhledávání chyb při programování v projektu služby SharePoint pomocí IntelliTrace.|
|[Testy jednotek kódu](../test/unit-test-your-code.md)|Popisuje, jak najít logické chyby ve vašem kódu pomocí testů jednotek.|

## <a name="see-also"></a>Viz také

- [Zlepšení kvality kódu](../test/improve-code-quality.md)