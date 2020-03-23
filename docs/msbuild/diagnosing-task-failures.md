---
title: Diagnostika selhání úloh | Dokumenty společnosti Microsoft
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89dcb8bddf2c92406ad5eff952d1f4050d7f9262
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593275"
---
# <a name="diagnosing-task-failures"></a>Diagnostikování selhání úloh

`MSB6006`je emitován, když odvozená <xref:Microsoft.Build.Utilities.ToolTask>třída - spustí proces nástroje, který vrací nenulový ukončovací kód, pokud úloha nezaeštila konkrétnější chybu.

## <a name="identifying-the-failing-task"></a>Identifikace selhání úkolu

Pokud narazíte na chybu úkolu, prvním krokem je identifikace úlohy, která selhává.

Text chyby určuje název nástroje (popisný název poskytnutý implementací úkolu <xref:Microsoft.Build.Utilities.ToolTask.ToolName> nebo název spustitelného souboru) a číselný ukončovací kód. Například v případě

```text
error MSB6006: "custom tool" exited with code 1.
```

Název nástroje `custom tool` je a ukončovací kód je `1`.

### <a name="command-line-builds"></a>Sestavení příkazového řádku

Pokud bylo sestavení nakonfigurováno tak, aby obsahovalo souhrn (výchozí), bude vypadat takto:

```text
Build FAILED.

"S:\MSB6006_demo\MSB6006_demo.csproj" (default target) (1) ->
(InvokeToolTask target) ->
  S:\MSB6006_demo\MSB6006_demo.csproj(19,5): error MSB6006: "custom tool" exited with code 1.
```

Tento výsledek znamená, že došlo k chybě v úkolu `S:\MSB6006_demo\MSB6006_demo.csproj`definovaném na `InvokeToolTask`řádku 19 souboru , v cíli s názvem , v projektu `S:\MSB6006_demo\MSB6006_demo.csproj`.

### <a name="in-visual-studio"></a>V nástroji Visual Studio

Stejné informace jsou k dispozici v seznamu `Project`chyb `File`sady `Line`Visual Studio ve sloupcích , a .

## <a name="finding-more-failure-information"></a>Hledání dalších informací o selhání

Tato chyba je vyzařována, pokud úloha nezaprotokolovala konkrétní chybu. Selhání protokolování chyby je často proto, že úloha není nakonfigurována tak, aby pochopila formát chyby vyzařovaný nástrojem, který volá.

Dobře vychované nástroje obvykle vyzařují některé kontextové nebo chybové informace do standardního výstupního nebo chybového proudu a úlohy zachycují a zaznamenávají tyto informace ve výchozím nastavení. Další informace naleznete v položkách protokolu ještě před tím, než došlo k chybě. K zachování těchto informací může být nutné znovu spustit sestavení s vyšší úrovní protokolu.

## <a name="next-steps"></a>Další kroky

Doufejme, že další kontext nebo chyby zjištěné v protokolování odhalí hlavní příčinu problému.

Pokud tomu tak není, bude pravděpodobně muset zúžit potenciální příčiny kontrolou vlastnosti a položky, které jsou vstupy k selhání úkolu.
