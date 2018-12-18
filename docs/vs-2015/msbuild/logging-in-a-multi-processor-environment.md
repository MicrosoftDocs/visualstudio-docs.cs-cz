---
title: Protokolování v prostředí s více procesory | Dokumentace Microsoftu
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
- MSBuild, multi-processor logging
- MSBuild, logging
ms.assetid: dd4dae65-ed04-4883-b48d-59bcb891c4dc
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc2a75c5aab920d6b2ab93ce53bc7f65263e8657
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49249662"
---
# <a name="logging-in-a-multi-processor-environment"></a>Protokolování v prostředí s více procesory
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Schopnost nástroje MSBuild používat více procesorů může výrazně zkrátit čas sestavení projektu, ale bude mít také za následek složitější protokolování. V prostředí s jedním procesorem může protokolovací nástroj zpracovat příchozí události, zprávy, upozornění a chyby předvídatelným, sekvenčním způsobem. Avšak v prostředí s více procesory mohou události přicházet z různých zdrojů zároveň nebo mimo pořadí. Nástroj MSBuild poskytuje nový protokolovací nástroj více-procesorů s ohledem na a povolí vytváření vlastních "předávajících protokolovacích nástrojů."  
  
## <a name="logging-multiple-processor-builds"></a>Protokolování víceprocesorových sestavení  
 Při sestavování jednoho nebo více projektů v systému s více procesory nebo s více jádry jsou události sestavení nástroje MSBuild pro všechny projekty generovány současně. Dorazit lavina dat událostí může do protokolovacího nástroje ve stejnou dobu nebo mimo pořadí. To můžete zahlcovat protokolovací nástroj a způsobit zvýšení doby sestavení, nesprávnému výstupu protokolovacího nástroje nebo dokonce k přerušení sestavení. Pro řešení těchto problémů, může protokolovací nástroj MSBuild zpracovávat události mimo pořadí a provádět korelaci událostí a jejich zdrojů.  
  
 Efektivitu protokolování lze ještě více zlepšit vytvořením vlastního předávajícího protokolovacího nástroje. Uživatelský předávající protokolovací nástroj funguje jako filtr tím, že umožňuje před sestavením zvolit události, které je třeba sledovat. Použitím vlastního předávajícího protokolovacího nástroje nedojde k zaplavení protokolovacího nástroje nechtěnými událostmi, nedojde k nadbytku při protokolování nebo zpomalení doby sestavení.  
  
### <a name="central-logging-model"></a>Model centrálního protokolování  
 Nástroj MSBuild používá pro víceprocesorová sestavení „model centrálního protokolování“. V modelu centrálního protokolování slouží instance nástroje MSBuild.exe jako primární proces sestavení nebo jako „centrální uzel“. Sekundární instance nástroje MSBuild.exe nebo též „sekundární uzly“ jsou připojeny k centrálnímu uzlu. Jakékoli protokolovací nástroje založené na nástroji ILogger, které jsou připojeny k centrálnímu uzlu, se nazývají „centrální protokolovací nástroje“, a protokolovací nástroje připojené k sekundárním uzlům se nazývají „sekundární protokolovací nástroje“.  
  
 Dojde-li k sestavení, sekundární protokolovací nástroje přesměrují svůj provoz událostí na centrální protokolovací nástroje. Vzhledem k tomu, že události pocházejí z několika sekundárních uzlů, přicházejí data do centrálního uzlu současně, avšak prokládaně. Chcete-li vyřešit odkazy událost na projekt a událost na cíl, obsahují argumenty události další kontextové informace události sestavení.  
  
 Přestože je třeba centrálním protokolovacím nástrojem implementovat pouze rozhraní <xref:Microsoft.Build.Framework.ILogger>, je doporučeno implementovat také rozhraní <xref:Microsoft.Build.Framework.INodeLogger>, aby bylo možné provést inicializaci centrálního protokolovacího nástroje s počtem uzlů, které se podílejí na sestavení. Při inicializaci protokolovacího nástroje je vyvoláno následující přetížení metody <xref:Microsoft.Build.Framework.ILogger.Initialize%2A>:  
  
```  
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
### <a name="distributed-logging-model"></a>Model distribuovaného protokolování  
 V modelu centrálního protokolování může příliš mnoho příchozích zpráv, například při sestavení mnoha projektů najednou, způsobit záplavu centrálního uzlu, což má za následek přetížení systému a snížení výkonu sestavení.  
  
 V rámci zmírnění tohoto problému nabízí nástroj MSBuild také „model distribuovaného protokolování“, který rozšiřuje model centrálního protokolování tím, že umožňuje vytvořit předávající protokolovací nástroje. Předávající protokolovací nástroj se připojuje k sekundárnímu uzlu a z daného uzlu přijímá příchozí události sestavení. Předávající protokolovací nástroj je stejný jako běžný protokolovací nástroj s výjimkou, že umožňuje filtrování událostí a přeposlání pouze požadovaných událostí do centrálního uzlu. Tím se sníží přenos zpráv do centrálního uzlu a zlepšuje se výkon.  
  
 Předávající protokolovací nástroj je možné vytvořit implementováním rozhraní <xref:Microsoft.Build.Framework.IForwardingLogger>, které je odvozeno z rozhraní <xref:Microsoft.Build.Framework.ILogger>. Rozhraní je definováno takto:  
  
```  
public interface IForwardingLogger: INodeLogger  
{  
    public IEventRedirector EventRedirector { get; set; }  
    public int NodeId { get; set; }  
}  
```  
  
 Chcete-li přeposílat události v předávajícím protokolovacím nástroji, je třeba volat metodu <xref:Microsoft.Build.Framework.IEventRedirector.ForwardEvent%2A> rozhraní <xref:Microsoft.Build.Framework.IEventRedirector>. Předejte příslušné argumenty <xref:Microsoft.Build.Framework.BuildEventArgs> nebo jejich odvozené části jako parametr.  
  
 Další informace najdete v tématu [vytváření předávání protokolovacích nástrojů](../msbuild/creating-forwarding-loggers.md).  
  
### <a name="attaching-a-distributed-logger"></a>Připojení distribuovaného protokolovacího nástroje  
 Chcete-li připojit distribuovaný protokolovací nástroj v sestavení příkazového řádku, je třeba použít přepínač `/distributedlogger` (nebo `/dl`). Formát pro zadávání názvů typů a tříd protokolovacího nástroje je stejný jako u přepínače `/logger` s tím rozdílem, že distribuovaný prokolovací nástroj je tvořen dvěma třídami protokolování: předávající protokolovací nástroj a centrální protokolovací nástroj. Následuje příklad připojení distribuovaného protokolovacího nástroje:  
  
```  
msbuild.exe *.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,  
Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,  
Culture=neutral  
```  
  
 Hvězdička (*) v přepínači `/dl` odděluje názvy dvou protokolovacích nástrojů.  
  
## <a name="see-also"></a>Viz také  
 [Protokolovací nástroje sestavení](../msbuild/build-loggers.md)   
 [Vytváření předávajících (sekundárních) protokolovacích nástrojů](../msbuild/creating-forwarding-loggers.md)





