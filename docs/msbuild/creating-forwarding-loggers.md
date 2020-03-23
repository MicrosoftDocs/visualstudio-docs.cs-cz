---
title: Vytváření záznamníků pro předávání | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, forwarding loggers
- MSBuild, logging
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 852b783129f130316de88580020e0139925ffb37
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634302"
---
# <a name="create-forwarding-loggers"></a>Vytvořit předávací úhozy kláves

Předávání úhozů zlepšit efektivitu protokolování tím, že umožňuje vybrat události, které chcete sledovat při vytváření projektů na víceprocesorový systém. Povolením předávání úhozů, můžete zabránit nežádoucí události z zahlcení centrální protokolování, zpomalení doby sestavení a zaneřádění protokolu.

 Chcete-li vytvořit předávání protokolování, <xref:Microsoft.Build.Framework.IForwardingLogger> můžete buď implementovat rozhraní a potom <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> implementovat jeho metody ručně, nebo použít třídu a její předkonfigurované metody. (Ten bude stačit pro většinu aplikací.)

## <a name="register-events-and-respond-to-them"></a>Registrace událostí a reakce na ně

 Předávání protokolování shromažďuje informace o události sestavení, jak jsou hlášeny sekundární modul sestavení, což je pracovní proces, který je vytvořen procesem hlavní sestavení během sestavení na více procesorového systému. Potom předávání protokolování vybere události dopředu centrální protokolování, na základě pokynů, které jste mu dali.

 Je nutné zaregistrovat předávání úhozy kláves pro zpracování událostí, které chcete sledovat. Chcete-li zaregistrovat události, úhozy kláves musí přepsat metodu. <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> Tato metoda nyní obsahuje `nodecount`volitelný parametr , který lze nastavit na počet procesorů v systému. (Ve výchozím nastavení je hodnota 1.)

 Příklady událostí, které <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>můžete <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>sledovat, jsou , a <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.

 V prostředí s více procesory jsou zprávy událostí pravděpodobně přijaty mimo pořadí. Proto je nutné vyhodnotit události pomocí obslužné rutiny události v předávání protokolů a naprogramovat ji k určení, které události předat přesměrovačpro předávání centrální protokolovací nástroj. Chcete-li to provést, <xref:Microsoft.Build.Framework.BuildEventContext> můžete použít třídu, která je připojena ke každé zprávě, k identifikaci událostí, které chcete předat dál, a pak předat názvy událostí <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> do třídy (nebo její podtřídy). Při použití této metody není nutné žádné jiné specifické kódování k předávání událostí.

## <a name="specify-a-forwarding-logger"></a>Určení protokolovacího nástroje pro předávání

 Po předávání protokolování byla zkompilována do sestavení, musíte říct MSBuild použít během sestavení. Chcete-li to `-FileLogger`provést, použijte , `-FileLoggerParameters`a `-DistributedFileLogger` přepínače spolu s *MSBuild.exe*. Přepínač `-FileLogger` říká *MSBuild.exe,* že protokolovací nástroj je přímo připojen. Přepínač `-DistributedFileLogger` znamená, že je soubor protokolu na uzel. Chcete-li nastavit parametry na předávání `-FileLoggerParameters` protokolování, použijte přepínač. Další informace o těchto a dalších přepínačích *MSBuild.exe* naleznete v [tématu Command-line reference](../msbuild/msbuild-command-line-reference.md).

## <a name="multi-processor-aware-loggers"></a>Víceprocesorové úhozy kláves

 Při vytváření projektu v systému s více procesory, sestavení zprávy z každého procesoru nejsou automaticky prokládány v jednotném pořadí. Místo toho je nutné vytvořit prioritu <xref:Microsoft.Build.Framework.BuildEventContext> seskupení zpráv pomocí třídy, která je připojena ke každé zprávě. Další informace o vytváření více procesorů naleznete [v tématu Protokolování v prostředí s více procesory](../msbuild/logging-in-a-multi-processor-environment.md).

## <a name="see-also"></a>Viz také

- [Získat protokoly sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Sestavení úhozů kláves](../msbuild/build-loggers.md)
- [Protokolování v prostředí s více procesory](../msbuild/logging-in-a-multi-processor-environment.md)