---
title: Získání protokolů sestavení pomocí msbuild | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: f756d432d9ff4d3824c1f1165c63710e4d10c2e9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594887"
---
# <a name="obtain-build-logs-with-msbuild"></a>Získání protokolů sestavení pomocí msbuildu

Pomocí přepínačů s MSBuild, můžete určit, kolik sestavení dat, které chcete zkontrolovat a zda chcete uložit data sestavení do jednoho nebo více souborů. Můžete také zadat vlastní protokolovací nástroj pro shromažďování dat sestavení. Informace o přepínačích příkazového řádku MSBuild, které toto téma nepokrývá, naleznete v [tématu Odkaz na příkazový řádek](../msbuild/msbuild-command-line-reference.md).

> [!NOTE]
> Pokud vytváříte projekty pomocí ide sady Visual Studio, můžete tyto sestavení řešit kontrolou protokolů sestavení. Další informace naleznete v [tématu Postup: Zobrazení, uložení a konfigurace souborů protokolu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="set-the-level-of-detail"></a>Nastavení úrovně podrobností

 Při vytváření projektu pomocí MSBuild bez zadání úrovně podrobností se ve výstupním protokolu zobrazí následující informace:

- Chyby, upozornění a zprávy, které jsou klasifikovány jako velmi důležité.

- Některé události stavu.

- Souhrn sestavení.

Pomocí přepínače **-verbosity** (**-v**) můžete určit, kolik dat se zobrazí ve výstupním protokolu. Pro řešení potíží použijte úroveň podrobností `detailed` buď`d`( `diagnostic` `diag`) nebo ( ), která poskytuje nejvíce informací.

Proces sestavení může být pomalejší při nastavení **-podrobnost** `detailed` a ještě pomalejší při nastavení **-podrobnost** na `diagnostic`.

```cmd
msbuild MyProject.proj -t:go -v:diag
```

### <a name="verbosity-settings"></a>Nastavení podrobností

Následující tabulka ukazuje, jak podrobnost protokolu (hodnoty sloupců) ovlivňuje, které typy zpráv (hodnoty řádků) jsou protokolovány.

|                                       | Quiet | Minimální | Normální | Detailed | Diagnostické |
|---------------------------------------|:-----:|:-------:|:------:|:--------:|:----------:|
| chyby                                |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Upozornění                              |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Zprávy s vysokou důležitostí              |       |    ✅    |    ✅   |     ✅    |      ✅     |
| Zprávy s normální důležitostí           |       |         |    ✅   |     ✅    |      ✅     |
| Zprávy s nízkou důležitostí              |       |         |        |     ✅    |      ✅     |
| Další informace o modulu MSBuild |       |         |        |          |      ✅     |

## <a name="save-the-build-log-to-a-file"></a>Uložení protokolu sestavení do souboru

Přepínač **-fileLogger** (**fl**) můžete použít k uložení dat sestavení do souboru. Následující příklad uloží data sestavení do souboru s názvem *msbuild.log*.

```cmd
msbuild MyProject.proj -t:go -fileLogger
```

 V následujícím příkladu je soubor protokolu pojmenován *MyProjectOutput.log*a podrobnost výstupu protokolu `diagnostic`je nastavena na . Tato dvě nastavení zadáte pomocí přepínače **parametry -filelogparameters** (`flp`).

```cmd
msbuild MyProject.proj -t:go -fl -flp:logfile=MyProjectOutput.log;verbosity=diagnostic
```

 Další informace naleznete v [tématu Command-line reference](../msbuild/msbuild-command-line-reference.md).

## <a name="save-the-log-output-to-multiple-files"></a>Uložení výstupu protokolu do více souborů

 Následující příklad uloží celý protokol do *msbuild1.log*, pouze chyby *JustErrors.log*a pouze upozornění *justwarnings.log*. Příklad používá čísla souborů pro každý ze tří souborů. Čísla souborů jsou určena hned za přepínači **-fl** a `-fl1` `-flp1` **-flp** (například a ).

 Přepínače **-filelogparameters** (`flp`) pro soubory 2 a 3 určují, co mají být pojmenovány jednotlivými soubory a co mají být zahrnuty do každého souboru. Pro soubor 1 není zadán žádný název, proto se používá výchozí název *souboru msbuild1.log.*

```cmd
msbuild MyProject.proj -t:go -fl1 -fl2 -fl3 -flp2:logfile=JustErrors.log;errorsonly -flp3:logfile=JustWarnings.log;warningsonly
```

 Další informace naleznete v [tématu Command-line reference](../msbuild/msbuild-command-line-reference.md).

## <a name="save-a-binary-log"></a>Uložení binárního protokolu

Můžete uložit log v komprimovaném, binárním formátu pomocí přepínače **-binaryLogger** (**bl).** Tento protokol obsahuje podrobný popis procesu sestavení a lze jej číst pomocí určitých nástrojů pro analýzu protokolu.

V následujícím příkladu je vytvořen binární soubor protokolu s názvem *binarylogfilename*.

```cmd
-bl:binarylogfilename.binlog
```

Další informace naleznete v [tématu Command-line reference](../msbuild/msbuild-command-line-reference.md).

## <a name="use-a-custom-logger"></a>Použití vlastního úhozu

 Můžete napsat vlastní protokolovací protokol tím, že <xref:Microsoft.Build.Framework.ILogger> authoring spravovaný typ, který implementuje rozhraní. Vlastní protokolovací diagram můžete například odeslat chyby sestavení v e-mailu, protokolovat je do databáze nebo je protokolovat do souboru XML. Další informace naleznete v [tématu Sestavení úhozů kláves](../msbuild/build-loggers.md).

 V příkazovém řádku MSBuild zadáte vlastní protokolování pomocí přepínače **-logger.** Můžete také použít přepínač **-noconsolelogger** k zakázání výchozího záznamníku konzoly.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.Build.Framework.LoggerVerbosity>
- [Sestavení úhozů kláves](../msbuild/build-loggers.md)
- [Protokolování v prostředí s více procesory](../msbuild/logging-in-a-multi-processor-environment.md)
- [Vytváření předávacích úhozů](../msbuild/creating-forwarding-loggers.md)
- [Koncepty MSBuild](../msbuild/msbuild-concepts.md)
