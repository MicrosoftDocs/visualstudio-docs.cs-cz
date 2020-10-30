---
title: Získání protokolů sestavení pomocí nástroje MSBuild | Microsoft Docs
description: Naučte se používat přepínače s nástrojem MSBuild k určení, kolik dat sestavení se má zkontrolovat a jestli se mají uložit data sestavení do jednoho nebo více souborů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf13e23d69dfeba967e8e971ad2463cef4546567
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048963"
---
# <a name="obtain-build-logs-with-msbuild"></a>Získání protokolů sestavení pomocí nástroje MSBuild

Pomocí přepínačů s nástrojem MSBuild můžete určit, kolik dat sestavení chcete zkontrolovat a zda chcete uložit data sestavení do jednoho nebo více souborů. Můžete také zadat vlastní protokolovací nástroj pro shromažďování dat buildu. Informace o přepínačích příkazového řádku MSBuild, které toto téma popisuje, najdete v tématu [Reference k příkazovému řádku](../msbuild/msbuild-command-line-reference.md).

> [!NOTE]
> Pokud vytváříte projekty pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio, můžete tyto sestavení řešit pomocí kontroly protokolů sestavení. Další informace najdete v tématu [Postup: zobrazení, uložení a konfigurace souborů protokolu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="set-the-level-of-detail"></a>Nastavit úroveň podrobností

 Při sestavování projektu pomocí nástroje MSBuild bez zadání úrovně podrobností se v protokolu výstupu zobrazí následující informace:

- Chyby, varování a zprávy, které jsou zařazeny do kategorie jako vysoce důležité.

- Některé události stavu.

- Souhrn sestavení.

Pomocí přepínače **-verbose** ( **-v** ) můžete určit, kolik dat se zobrazí ve výstupním protokolu. Pro řešení potíží použijte úroveň podrobností pro `detailed` ( `d` ) nebo `diagnostic` ( `diag` ), která poskytuje nejvíc informací.

Proces sestavení může být pomalejší, pokud nastavíte **-Podrobnosti** na `detailed` a dokonce pomaleji, když nastavíte úroveň **-verbose** na `diagnostic` .

```cmd
msbuild MyProject.proj -t:go -v:diag
```

### <a name="verbosity-settings"></a>Nastavení podrobností

Následující tabulka ukazuje, jak se protokoluje podrobnosti protokolu (hodnoty sloupce), které jsou protokolovány.

| Typ a podrobnosti zprávy              | Quiet | Minimální | Normální | Detailed | diagnostické |
|---------------------------------------|:-----:|:-------:|:------:|:--------:|:----------:|
| Chyby                                |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Upozornění                              |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Zprávy s vysokou důležitostí              |       |    ✅    |    ✅   |     ✅    |      ✅     |
| Zprávy normálního významu           |       |         |    ✅   |     ✅    |      ✅     |
| Zprávy s nízkou důležitostí              |       |         |        |     ✅    |      ✅     |
| Další informace o modulu MSBuild |       |         |        |          |      ✅     |

## <a name="save-the-build-log-to-a-file"></a>Uložení protokolu sestavení do souboru

K uložení dat buildu do souboru můžete použít přepínač **-** ( **FL** ). Následující příklad uloží data sestavení do souboru s názvem *MSBuild. log* .

```cmd
msbuild MyProject.proj -t:go -fileLogger
```

 V následujícím příkladu je soubor protokolu pojmenovaný *MyProjectOutput. log* a podrobnost výstupu protokolu je nastavená na `diagnostic` . Tato dvě nastavení určíte pomocí přepínače **-fileLoggerParameters** ( `flp` ).

```cmd
msbuild MyProject.proj -t:go -fl -flp:logfile=MyProjectOutput.log;verbosity=diagnostic
```

 Další informace najdete v tématu [Reference k příkazovému řádku](../msbuild/msbuild-command-line-reference.md).

## <a name="save-the-log-output-to-multiple-files"></a>Uložení výstupu protokolu do více souborů

 Následující příklad uloží celý protokol do *msbuild1. log* , jenom chyby *JustErrors. log* a jenom upozornění do *JustWarnings. log* . Příklad používá čísla souborů pro každý ze tří souborů. Čísla souborů jsou uvedena hned po přepínačích **-FL** a **-FLP** (například `-fl1` a `-flp1` ).

 Přepínače **-fileLoggerParameters** ( `flp` ) pro soubory 2 a 3 určují, co má každý soubor pojmenovat a co se má zahrnout do každého souboru. Pro soubor 1 není zadán žádný název, proto je použit výchozí název *msbuild1. log* .

```cmd
msbuild MyProject.proj -t:go -fl1 -fl2 -fl3 -flp2:logfile=JustErrors.log;errorsonly -flp3:logfile=JustWarnings.log;warningsonly
```

 Další informace najdete v tématu [Reference k příkazovému řádku](../msbuild/msbuild-command-line-reference.md).

## <a name="save-a-binary-log"></a>Uložit binární protokol

Protokol můžete uložit v komprimovaném binárním formátu pomocí přepínače **-binaryLogger** **(6248** ). Tento protokol obsahuje podrobný popis procesu sestavení a lze ho číst pomocí některých nástrojů pro analýzu protokolu.

V následujícím příkladu se vytvoří binární soubor protokolu s názvem *binarylogfilename* .

```cmd
-bl:binarylogfilename.binlog
```

Další informace najdete v tématu [Reference k příkazovému řádku](../msbuild/msbuild-command-line-reference.md).

## <a name="use-a-custom-logger"></a>Použití vlastního protokolovacího nástroje

 Vlastní protokolovací nástroj můžete napsat vytvářením spravovaného typu, který implementuje <xref:Microsoft.Build.Framework.ILogger> rozhraní. Pomocí vlastního protokolovacího nástroje můžete například odesílat chyby sestavení v e-mailu, přihlašovat je do databáze nebo do souboru XML. Další informace najdete v tématu [protokolovací nástroje sestavení](../msbuild/build-loggers.md).

 V příkazovém řádku MSBuild zadáte vlastní protokolovací nástroj pomocí přepínače **-protokolovacího** nástroje. Pomocí přepínače **-noconsolelogger** můžete také zakázat výchozí protokolovací nástroj konzoly.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.Build.Framework.LoggerVerbosity>
- [Protokolovací nástroje sestavení](../msbuild/build-loggers.md)
- [Protokolování v prostředí s více procesory](../msbuild/logging-in-a-multi-processor-environment.md)
- [Vytváření předávajících (sekundárních) protokolovacích nástrojů](../msbuild/creating-forwarding-loggers.md)
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
