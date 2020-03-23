---
title: Psaní Multi-Processor-Aware Úhozy kláves | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, multi-proc aware loggers
- multi-proc loggers
- loggers, multi-proc
ms.assetid: ff987d1b-1798-4803-9ef6-cc8fcc263516
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 886e012b026ef17b512a7e134d080382744783ef
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630744"
---
# <a name="write-multi-processor-aware-loggers"></a>Zápis víceprocesorových úhozů

Schopnost MSBuild využít více procesorů může snížit čas vytváření projektu, ale také přidává složitost k vytváření protokolování událostí. V prostředí s jedním procesorem události, zprávy, upozornění a chyby dorazí do protokolovacího nástroje předvídatelným, sekvenčním způsobem. V prostředí s více procesory však události z různých zdrojů mohou být doručeny ve stejnou dobu nebo mimo pořadí. Chcete-li zajistit pro tento, MSBuild poskytuje více procesorů vědomi protokolování a nový model protokolování a umožňuje vytvořit vlastní "předávání úhozů kláves."

## <a name="multi-processor-logging-challenges"></a>Výzvy v oblasti protokolování ve více procesorech

 Při vytváření jednoho nebo více projektů na více procesorů nebo více jádrového systému MSBuild sestavení události pro všechny projekty jsou generovány současně. Lavina zpráv o událostech může dorazit do záznamníku současně nebo mimo pořadí. Vzhledem k tomu, že protokolovací nástroj MSBuild 2.0 není určen ke zpracování této situace, může přemoci protokolování a způsobit zvýšené doby sestavení, nesprávný výstup protokolování nebo dokonce přerušené sestavení. Chcete-li tyto problémy vyřešit, protokolování (počínaje MSBuild 3.5) můžete zpracovat události mimo pořadí a korelovat události a jejich zdroje.

 Efektivitu protokolování lze ještě více zlepšit vytvořením vlastního předávajícího protokolovacího nástroje. Vlastní předávání protokolfunguje jako filtr tím, že vám umožní vybrat, před sestavením, pouze události, které chcete sledovat. Při použití vlastní předávání protokolování, nežádoucí události nelze přemoci protokolování, nepořádek protokoly nebo pomalé sestavení časy.

## <a name="multi-processor-logging-models"></a>Víceprocesorové modely protokolování

 Chcete-li zajistit problémy se sestavením související s více procesory, msbuild podporuje dva modely protokolování, centrální a distribuované.

### <a name="central-logging-model"></a>Centrální logovací model

 V modelu centrální protokolování jedna instance *MSBuild.exe* funguje jako "centrální uzel" a podřízené instance centrálního uzlu ("sekundární uzly") připojit k centrálníuzel, který mu pomůže provádět úlohy sestavení.

 ![Centrální logger model](../msbuild/media/centralnode.png "Centrálníuzel")

 Úhozy kláves různých typů, které se připojují k centrálnímu uzlu, se nazývají "centrální úhozy kláves". K centrálnímu uzlu lze současně připojit pouze jednu instanci každého typu protokolování.

 Dojde-li k sestavení, sekundární uzly směrují své události sestavení do centrálního uzlu. Centrální uzel směruje všechny své události a také sekundární uzly do jednoho nebo více připojených centrálních úhozů. Úhozy kláves pak vytvořit soubory protokolu, které jsou založeny na příchozí data.

 I <xref:Microsoft.Build.Framework.ILogger> když je vyžadována pouze implementovat centrální protokolování, doporučujeme také implementovat <xref:Microsoft.Build.Framework.INodeLogger> tak, aby centrální protokolování inicializuje s počtem uzlů, které se účastní sestavení. Následující přetížení <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> metody vyvolá při inicializaci modulu motoru.

```csharp
public interface INodeLogger: ILogger
{
    public void Initialize(IEventSource eventSource, int nodeCount);
}
```

 Všechny již <xref:Microsoft.Build.Framework.ILogger>existující založené úhozy kláves mohou fungovat jako centrální úhozy kláves a mohou se připojit k sestavení. Centrální úhozy kláves napsané bez explicitní podpory pro scénáře protokolování více procesorů a události mimo pořadí může přerušit sestavení nebo vytvořit nesmyslný výstup.

### <a name="distributed-logging-model"></a>Model distribuovaného protokolování

 V modelu centrální protokolování příliš mnoho příchozích zpráv provoz může zahltit centrální uzel, například při sestavení mnoha projektů ve stejnou dobu. To může stres systémové prostředky a snížit výkon sestavení. Chcete-li tento problém zmírnit, MSBuild podporuje model distribuované protokolování.

 ![Model distribuovaného protokolování](../msbuild/media/distnode.png "DistNode")

 Model distribuovaného protokolování rozšiřuje model centrálního protokolování tím, že umožňuje vytvořit protokolování předávání.

#### <a name="forwarding-loggers"></a>Předávání úhozů

 Předávání protokolování je sekundární, zjednodušené protokolování, který má filtr událostí, který se připojí k sekundární uzel a přijímá příchozí události sestavení z tohoto uzlu. Filtruje příchozí události a předá pouze ty, které zadáte do centrálního uzlu. To snižuje provoz zpráv, který je odeslán do centrálního uzlu a zlepšuje celkový výkon sestavení.

 Distribuované protokolování lze používat dvěma způsoby:

- Přizpůsobte pre-vyrobené předávání <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger>logger s názvem .

- Napište vlastní záznamník pro předávání.

Můžete upravit ConfigurableForwardingLogger tak, aby vyhovoval vašim požadavkům. Chcete-li to provést, volání úhozu na příkazovém řádku pomocí *MSBuild.exe*a seznam sestavení události, které chcete, aby protokolovací nástroj předávat do centrálního uzlu.

Jako alternativu můžete vytvořit vlastní předávání protokolování. Vytvořením vlastní předávání protokolování, můžete doladit chování protokolování. Vytvoření vlastního předávání protokolů je však složitější než pouze přizpůsobení KonfigurovatableForwardingLogger. Další informace naleznete v [tématu Vytváření předávacích úhozů](../msbuild/creating-forwarding-loggers.md).

## <a name="using-the-configurableforwardinglogger-for-simple-distributed-logging"></a>Použití konfigurovatelného forwardingloggeru pro jednoduché distribuované protokolování

 Chcete-li připojit konfigurovatelný forwardinglogger nebo vlastní předávání `-distributedlogger` protokolování, použijte přepínač (pro`-dl` krátké) v sestavení příkazového řádku *MSBuild.exe.* Formát pro určení názvy typů protokolování a tříd je `-logger` stejný jako pro přepínač, s tím rozdílem, že distribuovaný protokolování má vždy dvě třídy protokolování namísto jednoho, předávání protokolování a centrální protokolování. Následuje příklad, jak připojit vlastní předávání protokolování s názvem XMLForwardingLogger.

```cmd
msbuild.exe myproj.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,Culture=neutral
```

> [!NOTE]
> Hvězdička (*) musí oddělit dva názvy `-dl` úchytu v přepínači.

 Použití ConfigurableForwardingLogger je jako použití jakékoli jiné logger (jak je uvedeno v [Získání protokoly sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)), s tím rozdílem, že připojit KonfigurovatableForwardingLogger logger místo typické MSBuild logger a zadáte jako parametry události, které chcete ConfigurableForwardingLogger předat do centrálního uzlu.

 Například pokud chcete být upozorněni pouze v případě, že sestavení začíná a končí `BUILDSTARTEDEVENT` `BUILDFINISHEDEVENT`a `ERROREVENT` dojde k chybě, by předat , a jako parametry. Více parametrů může být předáno jejich oddělením s středníky. Následuje příklad použití konfigurovatelného nástroje ForwardingLogger k předávání `BUILDSTARTEDEVENT` `BUILDFINISHEDEVENT`pouze `ERROREVENT` událostí , a událostí.

```cmd
msbuild.exe myproj.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*ConfigureableForwardingLogger,C:\My.dll;BUILDSTARTEDEVENT; BUILDFINISHEDEVENT;ERROREVENT
```

 Následuje seznam dostupných parametrů ConfigurableForwardingLogger.

|Konfigurovatelné parametry forwardingloggeru|
| - |
|BUILDSTARTEDEVENT|
|BUILDFINISHEDEVENT|
|PROJEKTOVÁ UDÁLOST|
|PROJEKTDOKONČENÁUDÁLOST|
|UDÁLOST TARGETSTARTEDEVENT|
|CÍLFINISHEDEVENT|
|TASKSTARTEDEVENT|
|UDÁLOST DOKONČENÍ ÚKOLU|
|UDÁLOST CHYBY|
|UPOZORNĚNÍUDÁLOST|
|HIGHMESSAGEEVENT|
|UDÁLOST NORMÁLNÍ ZPRÁVY|
|UDÁLOST LOWMESSAGEEVENT|
|VLASTNÍ UDÁLOST|
|Commandline|
|SHRNUTÍ VÝKONU|
|NOSUMMARY|
|ZOBRAZIT PŘÍKAZ|

## <a name="see-also"></a>Viz také

- [Vytváření předávacích úhozů](../msbuild/creating-forwarding-loggers.md)