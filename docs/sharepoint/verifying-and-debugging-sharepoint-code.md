---
title: Zobrazení a ladění kódu služby SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- unit testing [SharePoint development in Visual Studio]
- IntelliTrace [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, IntelliTrace
- SharePoint development in Visual Studio, unit testing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 327e7be43fc60142fc50634ec61f6fd9499461e2
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120275"
---
# <a name="verify-and-debug-sharepoint-code"></a>Ověřte a ladění kódu služby SharePoint
Pomocí IntelliTrace a testování částí lze snadněji ladit řešení služby SharePoint a zajistit správnou funkčnost každé metody. Můžete tyto funkce pro projekty SharePoint v sadě Visual Studio podle stejné postupy jako jiné typy projektů.

## <a name="intellitrace"></a>Intellitrace
Pomocí IntelliTrace lze určit nejen aktuální stav řešení služby SharePoint, ale také událostí, ke kterým došlo v minulosti, a kontext, ve kterém k nim došlo. V řešení služby SharePoint lze přecházet zpět a vpřed do různých bodů, kdy byly zaznamenány události, a prohlížet stav a hodnoty proměnných v každém tomto bodě. Pomocí této dynamické navigace lze snadno a rychle ladit řešení služby SharePoint bez nutnosti nastavení mnoha zarážek. Relaci ladění si také můžete uložit do protokolu IntelliTrace (*.iTrace*) souboru, otevřete ho později ve Visual Studio Enterprise a provést po selhat ladění. *.ITrace* soubor obsahuje podrobné informace o kdy a kde se stalo konkrétní chyby služby SharePoint, takže můžete snadněji zjistit příčinu chyby. Informace v *.iTrace* souboru je podmnožinou protokolu dokončení chyb, který vytvoří Unified protokolování systému (ULS) ve službě SharePoint. Tyto informace zahrnují události, které jsou specifické pro službu SharePoint, například kdy byl otevřen nebo zavřen profil uživatele a kdy byly načteny, přečteny nebo změněny vlastnosti projektu služby SharePoint. Je možné nastavit, které události IntelliTrace zaznamená. Další informace najdete v tématu [pomocí uložit dat technologie IntelliTrace](/visualstudio/debugger/using-saved-intellitrace-data).

Dojde-li ve službě SharePoint k chybám, zobrazí dialogové okno identifikátor „ID korelace“ konkrétní chyby. Můžete také získat korelace ID události, které jsou uvedeny v *.iTrace* souboru. Pokud chcete zobrazit seznam všech událostí, které se stalo s danou korelační ID, můžete zadat ID v **Analysis** části souhrnná stránka IntelliTrace. V této části můžete zadat, zda chcete zobrazit pouze názvy událostí, ke kterým došlo, nebo názvy událostí a informace o jejich volání, dále název funkce, vstupní a výstupní body, parametry a návratové hodnoty.

Události v sadě Visual Studio můžete získat v IntelliTrace výběrem **F5** klíč. Chcete-li získat události, které jsou specifické pro službu SharePoint, musíte shromáždit data IntelliTrace v rámci řešení služby SharePoint pomocí nástroje Microsoft Monitoring Agent. Tento nástroj shromažďuje údaje o IntelliTrace a vytvoří *.iTrace* souborů pro aplikace, které jsou nasazeny mimo Visual Studio. Další informace najdete v tématu [funkce IntelliTrace](/visualstudio/debugger/intellitrace-features) a [pomocí samostatného kolektoru IntelliTrace](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector).

## <a name="unit-test"></a>Testování částí
Chyby lze v kódu snadněji vyhledat pomocí testování částí, ve kterých je kód psán a spouštěn v rámci testovacích metod. Tyto metody obsahují prázdné proměnné a kontrolní příkaz, který slouží k ověření logiky a funkčnosti projektu založeného na modelu objektu služby SharePoint. Další informace najdete v tématu [si kód Test jednotky](/visualstudio/test/unit-test-your-code).

### <a name="support-for-microsoft-fakes-framework"></a>Podpora pro Microsoft Fakes framework
Projekty služby SharePoint podporují Microsoft Fakes, což je izolované rozhraní, ve kterém lze vytvářet zkušební kódy na základě delegátů a překryvných ovladačů v aplikacích, které jsou založeny na rozhraní .NET Framework. Pomocí rozhraní Fakes lze vytvářet, spravovat a zakládat fiktivní implementace v rámci testování součástí. Tyto kódy a překryvné ovladače izolují testování částí od prostředí. Zkušební kód lze vytvářet pro testování kódu, který spotřebovává rozhraní nebo nezapečetěné třídy skrze přepisovatelné metody. Překryvné ovladače lze vytvořit pro přesměrování zapečetěných tříd se statickými metodami nebo metodami, které nelze přepsat do alternativní překryvné implementace. Zkušební kód a překryvné ovladače lze také použít pro dynamické nastavení chování jednotlivých zkušebních členů. Další informace najdete v tématu [izolace kódu v rámci testu s Microsoft Fakes](/visualstudio/test/isolating-code-under-test-with-microsoft-fakes).

## <a name="related-articles"></a>Související články

|Název|Popis|
|-----------|-----------------|
|[IntelliTrace](/visualstudio/debugger/intellitrace)|Tento článek popisuje snadnější ladění řešení aplikace Visual Studio pomocí IntelliTrace.|
|[Návod: Ladění aplikace SharePoint s použitím technologie IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|Znázorňuje způsob vyhledávání chyb při programování v projektu služby SharePoint pomocí IntelliTrace.|
|[Testování částí kódu](/visualstudio/test/unit-test-your-code)|Popisuje, jak najít logické chyby v kódu pomocí testování částí.|

## <a name="see-also"></a>Viz také:
[Zlepšení kvality kódu](/visualstudio/test/improve-code-quality)
