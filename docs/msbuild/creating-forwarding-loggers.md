---
title: Vytváření protokolovacích nástrojů pro předávání | Microsoft Docs
description: Vytváření protokolovacích nástrojů nástroje MSBuild pro zlepšení efektivity protokolování vám umožní vybrat události, které chcete monitorovat při sestavování projektů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, forwarding loggers
- MSBuild, logging
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0ffe175d9ea73640cae1197fe91656d3565525f6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901354"
---
# <a name="create-forwarding-loggers"></a>Vytváření protokolovacích nástrojů pro předávání

Přesměrování protokolovacích nástrojů zlepšují efektivitu protokolování tím, že vám umožní vybrat události, které chcete monitorovat při sestavování projektů v systému s více procesory. Povolením protokolovacích protokolovacích nástrojů můžete zabránit nechtěné události při zahlcení centrálního protokolovacího nástroje, zpomalení času sestavení a zaplnění vašeho protokolu.

 Chcete-li vytvořit protokolovací nástroj pro předávání, můžete buď implementovat <xref:Microsoft.Build.Framework.IForwardingLogger> rozhraní a pak implementovat jeho metody ručně, nebo použít <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> třídu a její předem nakonfigurované metody. (Ta bude stačit pro většinu aplikací.)

## <a name="register-events-and-respond-to-them"></a>Registrovat události a reagovat na ně

 Protokolovací nástroj pro předávání shromažďuje informace o událostech sestavení, které jsou hlášeny pomocí sekundárního sestavovacího modulu, což je pracovní proces, který je vytvořen hlavním procesem sestavení během sestavení v systému s více procesory. Protokolovací nástroj pro předávání pak vybere události, které se předají do centrálního protokolovacího nástroje, podle pokynů, které jste mu dali.

 Aby bylo možné zpracovávat události, které chcete monitorovat, je nutné zaregistrovat protokolovací nástroje pro předávání. K registraci pro události musí protokolovací nástroje přepsat <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> metodu. Tato metoda teď obsahuje volitelný parametr, `nodecount` který se dá nastavit na počet procesorů v systému. (Ve výchozím nastavení je tato hodnota 1.)

 Příklady událostí, které můžete monitorovat <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> , jsou, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> a <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> .

 V prostředí s více procesory je pravděpodobně zprávy o událostech přijímány mimo pořadí. Proto je nutné vyhodnotit události pomocí obslužné rutiny události v protokolovacím nástroji pro předávání a program, aby určil, které události předat přesměrovači pro přesměrování do centrálního protokolovacího nástroje. Chcete-li to provést, můžete použít <xref:Microsoft.Build.Framework.BuildEventContext> třídu, která je připojena ke každé zprávě, k identifikaci událostí, které chcete předat, a pak předat názvy událostí <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> třídě (nebo podtřídě IT). Když použijete tuto metodu, pro přeposílání událostí není nutné žádné jiné konkrétní kódování.

## <a name="specify-a-forwarding-logger"></a>Určení protokolovacího nástroje pro předávání

 Po zkompilování protokolovacího nástroje pro přeposílání do sestavení je nutné sdělit nástroji MSBuild, aby jej použil během sestavení. K tomu použijte `-FileLogger` `-FileLoggerParameters` přepínače, a `-DistributedFileLogger` společně s *MSBuild.exe*. `-FileLogger`Přepínač oznamuje *MSBuild.exe* , že je protokolovací nástroj přímo připojen. `-DistributedFileLogger`Přepínač znamená, že je k dispozici soubor protokolu na jeden uzel. K nastavení parametrů v protokolovacím nástroji pro přeposílání použijte `-FileLoggerParameters` přepínač. Další informace o těchto a dalších přepínačích *MSBuild.exe* najdete v tématu [Reference k příkazovému řádku](../msbuild/msbuild-command-line-reference.md).

## <a name="multi-processor-aware-loggers"></a>Protokolovací nástroje pracující s více procesory

 Při sestavování projektu v systému s více procesory nejsou zprávy sestavení z každého procesoru automaticky prolomeny v jednotném pořadí. Místo toho je nutné vytvořit prioritu seskupení zpráv pomocí <xref:Microsoft.Build.Framework.BuildEventContext> třídy, která je připojena ke každé zprávě. Další informace o sestavení s více procesory najdete v tématu [protokolování v prostředí s více](../msbuild/logging-in-a-multi-processor-environment.md)procesory.

## <a name="see-also"></a>Viz také

- [Získat protokoly sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Protokolovací nástroje sestavení](../msbuild/build-loggers.md)
- [Protokolování v prostředí s více procesory](../msbuild/logging-in-a-multi-processor-environment.md)