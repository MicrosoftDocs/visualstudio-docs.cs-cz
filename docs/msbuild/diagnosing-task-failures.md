---
title: Diagnostikování selhání úlohy | Microsoft Docs
description: Zjistěte, jak diagnostikovat selhání úloh nástroje MSBuild tím, že identifikujete úlohu s chybou, název nástroje a další informace.
ms.custom: SEO-VS-2020
ms.date: 09/25/2019
ms.topic: troubleshooting
f1_keywords:
- MSBuild.ToolTask.ToolCommandFailed
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 33aa8787144f185b5bcd2e26df5e7fa90ce3213f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877236"
---
# <a name="diagnosing-task-failures"></a>Diagnostikování selhání úloh

`MSB6006` je generována, když <xref:Microsoft.Build.Utilities.ToolTask> Třída – odvozené třídy spustí proces nástroje, který vrátí nenulový ukončovací kód v případě, že úloha neprotokoluje konkrétnější chybu.

## <a name="identifying-the-failing-task"></a>Identifikace úlohy, která selhala

Když narazíte na chybu úlohy, prvním krokem je identifikace úlohy, která selhává.

Text chyby Určuje název nástroje (popisný název poskytnutý implementací úlohy <xref:Microsoft.Build.Utilities.ToolTask.ToolName> nebo název spustitelného souboru) a číselný ukončovací kód. Například v

```text
error MSB6006: "custom tool" exited with code 1.
```

Název nástroje je `custom tool` a ukončovací kód je `1` .

### <a name="command-line-builds"></a>Sestavení z příkazového řádku

Pokud bylo sestavení nakonfigurované tak, aby zahrnovalo souhrn (výchozí nastavení), bude souhrn vypadat takto:

```text
Build FAILED.

"S:\MSB6006_demo\MSB6006_demo.csproj" (default target) (1) ->
(InvokeToolTask target) ->
  S:\MSB6006_demo\MSB6006_demo.csproj(19,5): error MSB6006: "custom tool" exited with code 1.
```

Tento výsledek indikuje, že došlo k chybě v úloze definované na řádku 19 souboru `S:\MSB6006_demo\MSB6006_demo.csproj` v cíli s názvem `InvokeToolTask` v projektu `S:\MSB6006_demo\MSB6006_demo.csproj` .

### <a name="in-visual-studio"></a>V nástroji Visual Studio

Stejné informace jsou k dispozici v seznamu chyb sady Visual Studio ve sloupcích `Project` , `File` a `Line` .

## <a name="finding-more-failure-information"></a>Hledání informací o dalších chybách

Tato chyba je vygenerována, pokud úloha neprotokoluje konkrétní chybu. Selhání při zaznamenání chyby je často způsobeno tím, že úloha není nakonfigurována pro pochopení formátu chyby generovaného nástrojem, který volá.

Dobře používané nástroje obecně generují určité kontextové nebo chybové informace ke svému standardnímu výstupnímu nebo chybovému proudu a úkoly zachytí a protokolují tyto informace ve výchozím nastavení. Pokud chcete získat další informace, podívejte se na položky protokolu, než došlo k chybě. Aby bylo možné zachovat tyto informace, může být nutné znovu spustit sestavení s vyšší úrovní protokolování.

## <a name="next-steps"></a>Další kroky

Snad, další kontext nebo chyby identifikované v protokolování odhalí hlavní příčinu problému.

Pokud ne, může být nutné omezit potenciální příčiny tím, že prozkoumáte vlastnosti a položky, které jsou vstupy pro úlohu, která selhala.
