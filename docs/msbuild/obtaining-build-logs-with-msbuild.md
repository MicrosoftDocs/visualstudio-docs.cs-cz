---
title: Získání protokolů pomocí nástroje MSBuild sestavení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 83f4de3efc64d78dd561a44fabed1e16f673d736
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879124"
---
# <a name="obtain-build-logs-with-msbuild"></a>Získání protokolů o sestavení pomocí nástroje MSBuild
S použitím přepínače pomocí nástroje MSBuild, můžete určit, kolik data sestavení, které chcete zkontrolovat a určuje, zda chcete uložit data sestavení do jednoho nebo více souborů. Můžete také určit vlastní protokolovací nástroj pro shromažďování dat sestavení. Informace o parametrech příkazového řádku MSBuild, které toto téma nepopisuje najdete v tématu [odkaz na příkazový řádek](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
>  Pokud vytváříte projekty s použitím rozhraní IDE sady Visual Studio, je možné řešit sestavení kontrolou protokolů o sestavení. Další informace najdete v tématu [postupy: zobrazení, ukládání a konfigurace souborů protokolu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
## <a name="set-the-level-of-detail"></a>Nastavte úroveň podrobností  
 Při vytváření projektu pomocí nástroje MSBuild bez zadání úroveň podrobností protokolu výstupu zobrazí následující informace:  
  
-   Chyby, varování a zprávy, které jsou klasifikovány jako vysoce důležité.  
  
-   Některé události stavu.  
  
-   Souhrn sestavení.  

S použitím **-podrobností** (**- v**) přepnout, můžete řídit, jak velký objem dat se zobrazí ve výstupu protokolu. S řešením problémů, použijte úroveň podrobností buď `detailed` (`d`) nebo `diagnostic` (`diag`), který poskytuje informace na maximum.  

Proces sestavení může být pomalejší, při nastavení **-podrobností** k `detailed` a dokonce i pomalejší, při nastavení **-podrobností** k `diagnostic`.  
  
```cmd  
msbuild MyProject.proj -t:go -v:diag  
```  

## <a name="save-the-build-log-to-a-file"></a>Uložit do protokolu sestavení do souboru  
 Můžete použít **- fileLogger** (**fl**) přepínač k uložení dat sestavení do souboru. Následující příklad uloží data sestavení do souboru s názvem *msbuild.log*.  
  
```cmd  
msbuild MyProject.proj -t:go -fileLogger  
```  
  
 V následujícím příkladu je soubor protokolu s názvem *MyProjectOutput.log*, a úroveň podrobností výstupu protokolu je nastavená na `diagnostic`. Tato dvě nastavení zadejte pomocí **- filelogparameters** (`flp`) přepnutí.  
  
```cmd  
msbuild MyProject.proj -t:go -fl -flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  
  
 Další informace najdete v tématu [odkaz na příkazový řádek](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="save-the-log-output-to-multiple-files"></a>Uložení výstupu protokolu do více souborů  
 V následujícím příkladu se uloží celý protokol *msbuild1.log*, jenom chyby do *JustErrors.log*a jenom oznámení, která *JustWarnings.log*. Příklad používá soubor čísla pro všechny tři soubory. Soubor čísla jsou hned za zadaný **-fl** a **- flp** přepínače (například `-fl1` a `-flp1`).  
  
 **- Filelogparameters** (`flp`) přepne pro soubory 2 a 3 zadat jak název každého souboru a co se má zahrnout do každého souboru. Není zadaný žádný název pro soubor 1, takže výchozí název *msbuild1.log* se používá.  
  
```cmd  
msbuild MyProject.proj -t:go -fl1 -fl2 -fl3 -flp2:logfile=JustErrors.log;errorsonly -flp3:logfile=JustWarnings.log;warningsonly  
  
```  
  
 Další informace najdete v tématu [odkaz na příkazový řádek](../msbuild/msbuild-command-line-reference.md).  

## <a name="save-a-binary-log"></a>Uložit binární protokol

V protokolu můžete uložit v komprimované binární formát pomocí **- binaryLogger** (**bl**) přepnutí. Tento protokol obsahuje podrobný popis procesu sestavení a může číst pomocí některých nástrojů pro analýzu protokolu.

V následujícím příkladu se vytvoří soubor binární protokolu s názvem *binarylogfilename*.

```cmd  
/bl:binarylogfilename.binlog
``` 
 
Další informace najdete v tématu [odkaz na příkazový řádek](../msbuild/msbuild-command-line-reference.md).  

## <a name="use-a-custom-logger"></a>Použít vlastní protokolovací nástroj  
 Můžete napsat vlastní protokolovací nástroj vytvořením spravovaného typu, který implementuje <xref:Microsoft.Build.Framework.ILogger> rozhraní. Můžete například použít vlastní protokolovací nástroj, odeslat chyby sestavení v e-mailu, připojit k databázi nebo protokolu do souboru XML. Další informace najdete v tématu [Protokolovací nástroje sestavení](../msbuild/build-loggers.md).  
  
 V příkazovém řádku nástroje MSBuild, zadejte vlastní protokolovací nástroj s použitím **-logger** přepnout. Můžete také použít **- noconsolelogger** přepínač, který zakáže výchozí protokolovací nástroj konzoly.  
  
## <a name="see-also"></a>Viz také:  
 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [Protokolovací nástroje sestavení](../msbuild/build-loggers.md)   
 [Protokolování v prostředí s více procesory](../msbuild/logging-in-a-multi-processor-environment.md)   
 [Vytváření předávající Protokolovací nástroje](../msbuild/creating-forwarding-loggers.md)   
 [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)