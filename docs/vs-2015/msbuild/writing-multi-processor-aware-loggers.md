---
title: Zápis více procesorů protokolovacích | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- msbuild, multi-proc aware loggers
- multi-proc loggers
- loggers, multi-proc
ms.assetid: ff987d1b-1798-4803-9ef6-cc8fcc263516
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b05c0f1782382f437a5e1d90bf19c724a05ca6a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49826371"
---
# <a name="writing-multi-processor-aware-loggers"></a>Zápis protokolovacích nástrojů pro více procesorů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Schopnost [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] výhod více procesorů může zkrátit čas sestavení projektu, ale také zvyšuje složitost vytváření protokolování událostí. V prostředí s jedním procesorem události, zprávy, upozornění a chyby do protokolovacího nástroje předvídatelným, sekvenčním způsobem. V prostředí s více procesory mohou však události z různých zdrojů dorazí, ve stejnou dobu nebo mimo pořadí. K poskytování v takovém případě [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] poskytuje více-procesorů s ohledem na protokolovací nástroj a nový model protokolování a umožňuje vám vytvořit vlastní "předávající Protokolovací nástroje".  
  
## <a name="multi-processor-logging-challenges"></a>Protokolování víceprocesorových výzvy  
 Při sestavování jednoho nebo více projektů v systému více procesory nebo s více jádry [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] události sestavení pro všechny projekty jsou generovány ve stejnou dobu. Dorazit lavina zprávy o událostech může do protokolovacího nástroje ve stejnou dobu nebo mimo pořadí. Protože [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 2.0 protokolovacího nástroje není určený ke zpracování této situaci, můžete zahlcovat protokolovací nástroj a způsobit zvýšení doby sestavení, nesprávnému výstupu protokolovacího nástroje nebo dokonce k přerušení sestavení. K vyřešení těchto problémů, protokolovacího nástroje (počínaje [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 3.5) můžete zpracovávat události mimo pořadí a provádět korelaci událostí a jejich zdrojů.  
  
 Efektivitu protokolování lze ještě více zlepšit vytvořením vlastního předávajícího protokolovacího nástroje. Vlastního předávajícího protokolovacího nástroje funguje jako filtr tím, že umožňuje před sestavením zvolit pouze události, kterou chcete monitorovat. Při použití vlastního předávajícího protokolovacího nástroje nechtěnými událostmi nelze zahlcovat protokolovač, nadbytku nebo zpomalení doby sestavení.  
  
## <a name="multi-processor-logging-models"></a>Modely protokolování pro více procesorů  
 Zajištění pro problémy se sestavením souvisejícím na více procesorů, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] podporuje dva modely protokolování, střední a distribuované.  
  
### <a name="central-logging-model"></a>Model centrálního protokolování  
 V modelu centrálního protokolování slouží jedné instance nástroje MSBuild.exe jako "centrální uzel" a podřízené instance do centrálního uzlu ("sekundární uzly") připojit k centrálnímu uzlu, což pomůže provádět úlohy sestavení.  
  
 ![Model centrálního protokolovacího nástroje](../msbuild/media/centralnode.png "CentralNode")  
  
 Protokolovací nástroje různých typů, která se připojit k centrálnímu uzlu se nazývají "centrální Protokolovací nástroje". Pouze jedna instance každého typu protokolovací nástroj může být připojen k centrálnímu uzlu ve stejnou dobu.  
  
 Pokud dojde k sestavení, sekundární uzly směrování událostí služby jejich sestavení k centrálnímu uzlu. Do centrálního uzlu směruje na jeden nebo více centrální Protokolovací nástroje připojené všechny jeho události i těch, které sekundární uzly. Protokolovací nástroje vytvořte soubory protokolů, které jsou založeny na příchozí data.  
  
 I když jediný <xref:Microsoft.Build.Framework.ILogger> je třeba centrálním protokolovacím nástrojem implementovat, doporučujeme vám také implementovat <xref:Microsoft.Build.Framework.INodeLogger> tak, aby centrální protokolovací nástroj se inicializuje s počtem uzlů, které se podílejí na sestavení. Následující přetížení <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> metoda vyvolá při inicializaci protokolovacího nástroje.  
  
```  
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
 Všechny existující <xref:Microsoft.Build.Framework.ILogger>– na základě protokolovacích nástrojů může fungovat jako centrální Protokolovací nástroje a může připojit k sestavení. Centrální Protokolovací nástroje, které jsou psány bez explicitní podporu pro scénáře protokolování pro více procesorů a události mimo pořadí však může přerušit sestavení nebo nemá význam výstup.  
  
### <a name="distributed-logging-model"></a>Model distribuovaného protokolování  
 V modelu centrálního protokolování může příliš mnoho příchozích zpráv lze záplavu centrálního uzlu, například při sestavení mnoha projektů najednou. To můžete zdůraznit systémových prostředků a snížení výkonu sestavení. K usnadnění tento problém [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] podporuje model distribuovaného protokolování.  
  
 ![Distribuované Model protokolování](../msbuild/media/distnode.png "DistNode")  
  
 Model distribuovaného protokolování rozšiřuje model centrálního protokolování tím, že umožňuje vytvořit předávající protokolovací nástroj.  
  
#### <a name="forwarding-loggers"></a>Předávání protokolovacích nástrojů  
 Předávající protokolovací nástroj je sekundární, zjednodušené protokolovač, který má filtr událostí, který se připojuje k sekundárnímu uzlu a z daného uzlu přijímá příchozí události sestavení. Filtruje příchozí události a předává pouze ty, které určíte k centrálnímu uzlu. To sníží přenos zpráv, který je odeslán do centrálního uzlu a zlepšuje celkový výkon sestavení.  
  
 Existují dva způsoby, jak pomocí distribuované protokolování, následujícím způsobem:  
  
- Přizpůsobení předem kovodělných předávající protokolovací nástroj s názvem <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger>.  
  
- Napište vlastní vlastního předávajícího protokolovacího nástroje.  
  
  Můžete upravit ConfigurableForwardingLogger tak, aby vyhovoval vašim požadavkům. K tomuto účelu volání protokolovací nástroj pomocí MSBuild.exe na příkazovém řádku a vypsat události sestavení, které chcete předat do centrálního uzlu protokolovacího nástroje.  
  
  Jako alternativu můžete vytvořit vlastního předávajícího protokolovacího nástroje. Vytvořením vlastního předávajícího protokolovacího nástroje můžete doladit tak chování protokolovacího nástroje. Vytvoření vlastního předávajícího protokolovacího nástroje je však mnohem složitější než pouze přizpůsobení ConfigurableForwardingLogger. Další informace najdete v tématu [vytváření předávání protokolovacích nástrojů](../msbuild/creating-forwarding-loggers.md).  
  
## <a name="using-the-configurableforwardinglogger-for-simple-distributed-logging"></a>Použití ConfigurableForwardingLogger pro jednoduché distribuované protokolování  
 K připojení ConfigurableForwardingLogger nebo vlastního předávajícího protokolovacího nástroje, použijte `/distributedlogger` přepnout (`/dl` zkráceně) v sestavení z příkazového řádku MSBuild.exe. Formát pro zadávání názvů typů protokolovacího nástroje a třídy je stejný jako u `/logger` přepnout, s tím rozdílem, že distribuovaného protokolovacího nástroje vždy se dvěma třídami protokolování místo jednoho předávající protokolovací nástroj a centrální protokolovací nástroj. Následuje příklad toho, jak se připojit s názvem XMLForwardingLogger vlastního předávajícího protokolovacího nástroje.  
  
```  
msbuild.exe myproj.proj/distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,Culture=neutral  
```  
  
> [!NOTE]
>  Hvězdička (*) musí oddělovat názvy dvou protokolovacích v `/dl` přepnout.  
  
 Použití ConfigurableForwardingLogger se podobá použití jiných protokolovacího nástroje (jak je uvedeno v [získávání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)), s tím rozdílem, že připojíte protokolovač ConfigurableForwardingLogger místo typické [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] protokolovací nástroj a zadejte jako parametry události, které chcete ConfigurableForwardingLogger předat do centrálního uzlu.  
  
 Například, pokud chcete informovat pouze v případě, že sestavení začíná a končí, a pokud dojde k chybě, předejte `BUILDSTARTEDEVENT`, `BUILDFINISHEDEVENT`, a `ERROREVENT` jako parametry. Více parametrů je možné předat jejich oddělením středníkem. Následuje příklad, jak používat ConfigurableForwardingLogger předávat jenom `BUILDSTARTEDEVENT`, `BUILDFINISHEDEVENT`, a `ERROREVENT` události.  
  
```  
msbuild.exe myproj.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*ConfigureableForwardingLogger,C:\My.dll;BUILDSTARTEDEVENT; BUILDFINISHEDEVENT;ERROREVENT  
```  
  
 Následuje seznam dostupných parametrů ConfigurableForwardingLogger.  
  
|Parametry ConfigurableForwardingLogger|  
|---------------------------------------------|  
|BUILDSTARTEDEVENT|  
|BUILDFINISHEDEVENT|  
|PROJECTSTARTEDEVENT|  
|PROJECTFINISHEDEVENT|  
|TARGETSTARTEDEVENT|  
|TARGETFINISHEDEVENT|  
|TASKSTARTEDEVENT|  
|TASKFINISHEDEVENT|  
|ERROREVENT|  
|WARNINGEVENT|  
|HIGHMESSAGEEVENT|  
|NORMALMESSAGEEVENT|  
|LOWMESSAGEEVENT|  
|CUSTOMEVENT|  
|PŘÍKAZOVÝ ŘÁDEK|  
|PERFORMANCESUMMARY|  
|NOSUMMARY|  
|SHOWCOMMANDLINE|  
  
## <a name="see-also"></a>Viz také  
 [Vytváření předávajících (sekundárních) protokolovacích nástrojů](../msbuild/creating-forwarding-loggers.md)



