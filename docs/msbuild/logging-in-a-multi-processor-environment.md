---
title: Přihlášení do prostředí s více procesory | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, multi-processor logging
- MSBuild, logging
ms.assetid: dd4dae65-ed04-4883-b48d-59bcb891c4dc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0c332fb67e96bdfea0059de11441da7c32871633
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633561"
---
# <a name="logging-in-a-multi-processor-environment"></a>Protokolování v prostředí s více procesory

Schopnost nástroje MSBuild používat více procesorů může výrazně zkrátit čas sestavení projektu, ale bude mít také za následek složitější protokolování. V prostředí s jedním procesorem může protokolovací nástroj zpracovat příchozí události, zprávy, upozornění a chyby předvídatelným, sekvenčním způsobem. Avšak v prostředí s více procesory mohou události přicházet z různých zdrojů zároveň nebo mimo pořadí. MSBuild poskytuje nový protokolovací nástroj podporující více procesorů a umožňuje vytvoření vlastních "předávání úhozů kláves.".

## <a name="log-multiple-processor-builds"></a>Protokolovat sestavení s více procesory

Při sestavování jednoho nebo více projektů v systému s více procesory nebo s více jádry jsou události sestavení nástroje MSBuild pro všechny projekty generovány současně. Lavina dat o událostech může dorazit do záznamníku ve stejnou dobu nebo mimo pořadí. To může zahltit protokolování a způsobit zvýšené doby sestavení, nesprávný výstup protokolování nebo dokonce přerušené sestavení. Chcete-li tyto problémy vyřešit, msbuild logger můžete zpracovat události mimo pořadí a korelovat události a jejich zdroje.

Efektivitu protokolování lze ještě více zlepšit vytvořením vlastního předávajícího protokolovacího nástroje. Uživatelský předávající protokolovací nástroj funguje jako filtr tím, že umožňuje před sestavením zvolit události, které je třeba sledovat. Použitím vlastního předávajícího protokolovacího nástroje nedojde k zaplavení protokolovacího nástroje nechtěnými událostmi, nedojde k nadbytku při protokolování nebo zpomalení doby sestavení.

### <a name="central-logging-model"></a>Centrální logovací model

Nástroj MSBuild používá pro víceprocesorová sestavení „model centrálního protokolování“. V modelu centrální protokolování instance *MSBuild.exe* funguje jako primární proces sestavení nebo "centrální uzel.". Sekundární instance *msbuild.exe*nebo "sekundární uzly" jsou připojeny k centrálnímu uzlu. Jakékoli protokolovací nástroje založené na nástroji ILogger, které jsou připojeny k centrálnímu uzlu, se nazývají „centrální protokolovací nástroje“, a protokolovací nástroje připojené k sekundárním uzlům se nazývají „sekundární protokolovací nástroje“.

Dojde-li k sestavení, sekundární protokolovací nástroje přesměrují svůj provoz událostí na centrální protokolovací nástroje. Vzhledem k tomu, že události pocházejí z několika sekundárních uzlů, přicházejí data do centrálního uzlu současně, avšak prokládaně. Chcete-li vyřešit odkazy událost na projekt a událost na cíl, obsahují argumenty události další kontextové informace události sestavení.

Přestože je třeba centrálním protokolovacím nástrojem implementovat pouze rozhraní <xref:Microsoft.Build.Framework.ILogger>, je doporučeno implementovat také rozhraní <xref:Microsoft.Build.Framework.INodeLogger>, aby bylo možné provést inicializaci centrálního protokolovacího nástroje s počtem uzlů, které se podílejí na sestavení. Při inicializaci protokolovacího nástroje je vyvoláno následující přetížení metody <xref:Microsoft.Build.Framework.ILogger.Initialize%2A>:

```csharp
public interface INodeLogger: ILogger
{
    public void Initialize(IEventSource eventSource, int nodeCount);
}
```

### <a name="distributed-logging-model"></a>Model distribuovaného protokolování

V modelu centrálního protokolování může příliš mnoho příchozích zpráv, například při sestavení mnoha projektů najednou, způsobit záplavu centrálního uzlu, což má za následek přetížení systému a snížení výkonu sestavení.

V rámci zmírnění tohoto problému nabízí nástroj MSBuild také „model distribuovaného protokolování“, který rozšiřuje model centrálního protokolování tím, že umožňuje vytvořit předávající protokolovací nástroje. Předávající protokolovací nástroj se připojuje k sekundárnímu uzlu a z daného uzlu přijímá příchozí události sestavení. Předávající protokolovací nástroj je stejný jako běžný protokolovací nástroj s výjimkou, že umožňuje filtrování událostí a přeposlání pouze požadovaných událostí do centrálního uzlu. Tím se sníží přenos zpráv do centrálního uzlu a zlepšuje se výkon.

 Předávající protokolovací nástroj je možné vytvořit implementováním rozhraní <xref:Microsoft.Build.Framework.IForwardingLogger>, které je odvozeno z rozhraní <xref:Microsoft.Build.Framework.ILogger>. Rozhraní je definováno takto:

```csharp
public interface IForwardingLogger: INodeLogger
{
    public IEventRedirector EventRedirector { get; set; }
    public int NodeId { get; set; }
}
```

Chcete-li přeposílat události v předávajícím protokolovacím nástroji, je třeba volat metodu <xref:Microsoft.Build.Framework.IEventRedirector.ForwardEvent%2A> rozhraní <xref:Microsoft.Build.Framework.IEventRedirector>. Předejte příslušné argumenty <xref:Microsoft.Build.Framework.BuildEventArgs> nebo jejich odvozené části jako parametr.

Další informace naleznete v [tématu Vytvoření předávacích úhozů](../msbuild/creating-forwarding-loggers.md).

### <a name="attaching-a-distributed-logger"></a>Připojení distribuovaného záznamníku

Chcete-li připojit distribuovaný protokolovací nástroj v sestavení příkazového řádku, je třeba použít přepínač `-distributedlogger` (nebo `-dl`). Formát pro zadávání názvů typů a tříd protokolovacího nástroje je stejný jako u přepínače `-logger` s tím rozdílem, že distribuovaný prokolovací nástroj je tvořen dvěma třídami protokolování: předávající protokolovací nástroj a centrální protokolovací nástroj. Následuje příklad připojení distribuovaného protokolovacího nástroje:

```cmd
msbuild.exe *.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,
Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,
Culture=neutral
```

Hvězdička (*) v přepínači `-dl` odděluje názvy dvou protokolovacích nástrojů.

## <a name="see-also"></a>Viz také

- [Sestavení úhozů kláves](../msbuild/build-loggers.md)
- [Vytvořit předávací úhozy kláves](../msbuild/creating-forwarding-loggers.md)
