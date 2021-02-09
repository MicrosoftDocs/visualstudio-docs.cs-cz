---
title: Zápis protokolovacích nástrojů s více procesory | Microsoft Docs
description: Naučte se, jak MSBuild poskytuje protokolovací a protokolovací model s více procesory, a umožňuje vytvářet vlastní "předávací protokolovací nástroje".
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, multi-proc aware loggers
- multi-proc loggers
- loggers, multi-proc
ms.assetid: ff987d1b-1798-4803-9ef6-cc8fcc263516
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1e7cf5998645230f038c6de12c79b53b44c09dfc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847983"
---
# <a name="write-multi-processor-aware-loggers"></a>Zápis protokolovacích nástrojů s více procesory

Schopnost nástroje MSBuild využít výhod více procesorů může zkrátit dobu sestavování projektu, ale také přináší složitost pro protokolování událostí sestavení. V prostředí s jedním procesorem, události, zprávy, upozornění a chyby dorazí do protokolovacího nástroje předvídatelným sekvenčním způsobem. V prostředí s více procesory ale můžou události z různých zdrojů dorazit ve stejnou dobu nebo mimo pořadí. Za tímto účelem nástroj MSBuild poskytuje protokolovací nástroj s podporou více procesorů a nový model protokolování a umožňuje vytvořit vlastní "předávací protokolovací nástroje".

## <a name="multi-processor-logging-challenges"></a>Výzvy k protokolování s více procesory

 Při sestavování jednoho nebo více projektů v systému s více procesory nebo s více jádry jsou generovány události sestavení nástroje MSBuild pro všechny projekty ve stejnou dobu. Avalanche zpráv událostí může přijít do protokolovacího nástroje ve stejnou dobu nebo mimo pořadí. Vzhledem k tomu, že protokolovací nástroj MSBuild 2,0 není navržený tak, aby zpracovávala tuto situaci, může přerušit protokolovací nástroj a způsobit zvýšené časy sestavení, nesprávný výstup protokolovacího nástroje nebo dokonce i přerušené sestavení. Aby bylo možné tyto problémy vyřešit, protokolovací nástroj (začínající v MSBuild 3,5) může zpracovávat události mimo pořadí a korelovat události a jejich zdroje.

 Efektivitu protokolování lze ještě více zlepšit vytvořením vlastního předávajícího protokolovacího nástroje. Vlastní protokolovací nástroj pro přesměrování funguje jako filtr tím, že vám umožní vybrat, ještě než začnete vytvářet, jenom události, které chcete monitorovat. Při použití vlastního protokolovacího nástroje pro předávání nemůžou nechtěné události přesměrovat protokolovací nástroj, zbytečně zastavovat protokoly nebo zpomalovat časy sestavení.

## <a name="multi-processor-logging-models"></a>Modely protokolování s více procesory

 Pro zajištění potíží s sestavením s více procesory podporuje nástroj MSBuild dva modely protokolování, Central a distribuované.

### <a name="central-logging-model"></a>Model centrálního protokolování

 V modelu centrálního protokolování se jedna instance *MSBuild.exe* chová jako "centrální uzel" a podřízené instance centrálního uzlu ("sekundární uzly") se připojují k centrálnímu uzlu, který jim usnadní provádění úloh sestavení.

 ![Model centrálního protokolovacího nástroje](../msbuild/media/centralnode.png "CentralNode")

 Protokolovací nástroje různých typů, které se připojují k centrálnímu uzlu, se nazývají "centrální protokolovací nástroje". Pouze jedna instance každého typu protokolovacího nástroje může být současně připojena k centrálnímu uzlu.

 Když dojde k sestavení, sekundární uzly směrují své události sestavení do centrálního uzlu. Centrální uzel směruje všechny své události a také sekundární uzly na jeden nebo více připojených centrálních protokolovacích nástrojů. Protokolovací nástroje pak vytvoří soubory protokolů, které jsou založeny na příchozích datech.

 I když <xref:Microsoft.Build.Framework.ILogger> je nutné, aby byl implementován pouze pomocí centrálního protokolovacího nástroje, doporučujeme implementovat také, aby se <xref:Microsoft.Build.Framework.INodeLogger> centrální protokolovací nástroj inicializuje s počtem uzlů, které se účastní sestavení. Následující přetížení <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> metody vyvolá v případě, že modul inicializuje protokolovací nástroj.

```csharp
public interface INodeLogger: ILogger
{
    public void Initialize(IEventSource eventSource, int nodeCount);
}
```

 Jakékoli již existující <xref:Microsoft.Build.Framework.ILogger> protokolovací nástroje můžou fungovat jako centrální protokolovací nástroje a můžou se připojit k sestavení. Centrální protokolovací nástroje zapsané bez explicitní podpory scénářů protokolování ve více procesorech a události mimo pořadí ale můžou přerušit sestavení nebo vytvářet nevýznamné výstupy.

### <a name="distributed-logging-model"></a>Model distribuovaného protokolování

 V modelu centrálního protokolování může příliš mnoho přenosů příchozích zpráv způsobit zahlcení centrálního uzlu, například při sestavení mnoha projektů ve stejnou dobu. To může nastresovat systémové prostředky a snížit výkon sestavení. Pro usnadnění tohoto problému nástroj MSBuild podporuje model distribuovaného protokolování.

 ![Model distribuovaného protokolování](../msbuild/media/distnode.png "DistNode")

 Model distribuovaného protokolování rozšiřuje model centrálního protokolování tím, že vám umožní vytvořit protokolovací nástroj pro předávání.

#### <a name="forwarding-loggers"></a>Přesměrování protokolovacích nástrojů

 Protokolovací nástroj pro předávání je sekundární a odlehčený protokolovací nástroj, který má filtr událostí, který se připojuje k sekundárnímu uzlu a přijímá příchozí události sestavení z tohoto uzlu. Filtruje příchozí události a předává pouze ty, které zadáte do centrálního uzlu. Tím se snižuje přenos zpráv odeslaných do centrálního uzlu a zlepšuje se celkový výkon sestavení.

 Existují dva způsoby, jak distribuované protokolování použít, a to takto:

- Přizpůsobení předem připraveného protokolovacího nástroje pro předávání s názvem <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> .

- Napište si vlastní protokolovací nástroj pro přesměrování.

ConfigurableForwardingLogger můžete upravit tak, aby vyhovovaly vašim požadavkům. Chcete-li to provést, zavolejte protokolovací nástroj na příkazovém řádku pomocí *MSBuild.exe* a uveďte události sestavení, které má protokolovací nástroj předávat do centrálního uzlu.

Jako alternativu můžete vytvořit vlastní protokolovací nástroj pro předávání. Vytvořením vlastního protokolovacího nástroje pro předávání můžete vyladit chování protokolovacího nástroje. Vytvoření vlastního protokolovacího nástroje pro přesměrování je ale složitější než přizpůsobení ConfigurableForwardingLogger. Další informace najdete v tématu [vytváření protokolovacích](../msbuild/creating-forwarding-loggers.md)nástrojů pro předávání.

## <a name="using-the-configurableforwardinglogger-for-simple-distributed-logging"></a>Použití ConfigurableForwardingLogger pro jednoduché distribuované protokolování

 Chcete-li připojit ConfigurableForwardingLogger nebo vlastní protokolovací nástroj pro předávání, použijte `-distributedlogger` přepínač ( `-dl` pro krátký) v sestavení příkazového řádku *MSBuild.exe* . Formát pro zadání názvů typů a tříd protokolovacího nástroje je stejný jako u `-logger` přepínače, s tím rozdílem, že distribuovaný protokolovací nástroj má vždy dvě třídy protokolování namísto jednoho, protokolovacího nástroje pro předávání a centrálního protokolovacího nástroje. Následuje příklad připojení vlastního protokolovacího nástroje pro předávání s názvem XMLForwardingLogger.

```cmd
msbuild.exe myproj.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,Culture=neutral
```

> [!NOTE]
> Hvězdička (*) musí oddělit dva názvy protokolovacích nástrojů v `-dl` přepínači.

 Použití ConfigurableForwardingLogger se podobá použití jakéhokoli jiného protokolovacího nástroje (jak je uvedeno v části [získání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)), s tím rozdílem, že přidáváte protokolovací nástroj ConfigurableForwardingLogger namísto typického protokolovacího nástroje MSBuild a zadáte jako parametry události, které má ConfigurableForwardingLogger předat do centrálního uzlu.

 Například pokud chcete být upozorněni pouze v případě, že sestavení začíná a končí a když dojde k chybě, předáte `BUILDSTARTEDEVENT` , `BUILDFINISHEDEVENT` a `ERROREVENT` jako parametry. Více parametrů lze předat jejich oddělením středníkem. Následující příklad ukazuje, jak používat ConfigurableForwardingLogger k přeposílání pouze `BUILDSTARTEDEVENT` `BUILDFINISHEDEVENT` událostí, a `ERROREVENT` .

```cmd
msbuild.exe myproj.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*ConfigureableForwardingLogger,C:\My.dll;BUILDSTARTEDEVENT; BUILDFINISHEDEVENT;ERROREVENT
```

 Následuje seznam dostupných parametrů ConfigurableForwardingLogger.

|Parametry ConfigurableForwardingLogger|
| - |
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
|ŘÁDEK|
|PERFORMANCESUMMARY|
|Souhrn|
|SHOWCOMMANDLINE|

## <a name="see-also"></a>Viz také

- [Vytváření předávajících (sekundárních) protokolovacích nástrojů](../msbuild/creating-forwarding-loggers.md)