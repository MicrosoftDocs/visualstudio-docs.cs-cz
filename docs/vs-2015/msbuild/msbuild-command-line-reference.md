---
title: Odkaz na příkazový řádek MSBuild | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, msbuild.exe
- MSBuild, command line reference
- msbuild.exe
ms.assetid: edaa65ec-ab8a-42a1-84cb-d76d5b2f4584
caps.latest.revision: 61
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a1827166829686801743ccc98156a0009e50dc3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245905"
---
# <a name="msbuild-command-line-reference"></a>Referenční dokumentace pro použití nástroje MSBuild v příkazovém řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Použijete-li k sestavení projektu nebo řešení souboru MSBuild.exe, může obsahovat několik přepínačů určit různé aspekty procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
MSBuild.exe [Switches] [ProjectFile]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Argument|Popis|  
|--------------|-----------------|  
|`ProjectFile`|Sestavení cíle v souboru projektu, který zadáte. Pokud nezadáte soubor projektu, MSBuild vyhledá aktuální pracovní adresář pro příponu názvu souboru, který končí na "proj" a použije tento soubor. Můžete také určit soubor řešení sady Visual Studio pro tento argument.|  
  
## <a name="switches"></a>Přepínače  
  
|Přepínač|Krátký tvar|Popis|  
|------------|----------------|-----------------|  
|/help|/? nebo/h|Zobrazit informace o využití. Následující příkaz je příklad:<br /><br /> `msbuild.exe /?`|  
|/detailedsummary|/DS|Zobrazit podrobnosti o na konci do protokolu sestavení konfigurace, které byly vytvořeny a jak byly naplánovány na uzly.|  
|/ignoreprojectextensions: `extensions`|/ Ignorovat: `extensions`|Zadaným rozšířením ignorujte při určování, které soubor projektu pro sestavení. K oddělení více rozšíření, jak ukazuje následující příklad použijte středníky nebo čárkami:<br /><br /> `/ignoreprojectextensions:.vcproj,.sln`|  
|/ maxcpucount [:`number`]|/m[:`number`]|Určuje maximální počet souběžných procesů pro použití při vytváření. Pokud nezadáte tento přepínač, výchozí hodnota je 1. Zadáte-li tento přepínač bez zadání hodnoty, bude nástroj MSBuild použít až počet procesorů v počítači. Další informace najdete v tématu [sestavování více projektů současně](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).<br /><br /> Následující příklad nastaví nástroj MSBuild pro sestavení pomocí tří procesů MSBuild, což umožní tří projektů k sestavení ve stejnou dobu:<br /><br /> `msbuild myproject.proj /maxcpucount:3`|  
|/noautoresponse|/noautorsp|Neobsahují žádné soubory MSBuild.rsp automaticky.|  
|/nodeReuse:`value`|/nr:`value`|Povolit nebo zakázat opakované použití uzly nástroje MSBuild. Můžete zadat následující hodnoty:<br /><br /> -   **Hodnota TRUE**. Uzly zůstat po dokončení sestavení tak, aby sestaveních je můžete využít (výchozí).<br />-   **False**. Uzly není zůstat po dokončení sestavení.<br /><br /> Uzel odpovídá projekt, který je spuštěn. Pokud zahrnete **/maxcpucount** přepínače, více uzly mohou být prováděna současně.|  
|/nologo||Nezobrazovat úvodní nápis a zprávu o autorských právech.|  
|/ předzpracování [:`filepath`]|/pp[:`filepath`]|Vytvořte soubor projektu jeden, agregované podle vkládání všechny soubory, které by byl importován během sestavení, jejich hranic označené. Tento přepínač můžete snadněji určit, které soubory se importují, ze které soubory se importují a které soubory přispívají k sestavení. Pokud použijete tento přepínač, projekt není sestaven.<br /><br /> Pokud zadáte `filepath`, agregované projektu souboru je výstup do souboru. V opačném případě se zobrazí výstup v okně konzoly.<br /><br /> Informace o tom, jak používat `Import` element soubor projektu lze vložit do jiného souboru projektu, viz [Import – Element (MSBuild)](../msbuild/import-element-msbuild.md) a [postupy: použití stejného cíle ve více souborech projektu](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).|  
|/Property:`name`=`value`|/ p:`name`=`value`|Nastavení nebo přepsat zadané vlastnosti na úrovni projektu, kde `name` je název vlastnosti a `value` je hodnota vlastnosti. Zadejte každou vlastnost samostatně, nebo použijte středníky nebo čárkami k oddělení více vlastností, jako v následujícím příkladu:<br /><br /> `/property:WarningLevel=2;OutDir=bin\Debug`|  
|/ target:`targets`|t:`targets`|Sestavení zadaným cílům v projektu. Zadejte každý cíl samostatně, nebo použijte středníky nebo čárkami k oddělení více cílů, jako v následujícím příkladu:<br /><br /> `/target:Resources;Compile`<br /><br /> Pokud zadáte pomocí tohoto přepínače veškerých cílů, namísto veškerých cílů v jejich spuštění `DefaultTargets` atributu v souboru projektu. Další informace najdete v tématu [pořadí sestavení cílů](../msbuild/target-build-order.md) a [jak: Určete který cíl sestavení první](../msbuild/how-to-specify-which-target-to-build-first.md).<br /><br /> Cíl je skupina úloh. Další informace najdete v tématu [cíle](../msbuild/msbuild-targets.md).|  
|/toolsversion:`version`|/TV:`version`|Určuje verzi sady nástrojů, které chcete použít k sestavení projektu, jako v následujícím příkladu: `/toolsversion:3.5`<br /><br /> Pomocí tohoto přepínače můžete sestavit projekt a určit verzi, která se liší od verze zadaná v [Project – Element (MSBuild)](../msbuild/project-element-msbuild.md). Další informace najdete v tématu [přepsání nastavení ToolsVersion](../msbuild/overriding-toolsversion-settings.md).<br /><br /> Pro 4.5 nástroje MSBuild, můžete zadat následující hodnoty pro `version`: 2.0, 3.5 a 4.0. Pokud zadáte 4.0, `VisualStudioVersion` vlastnost sestavení určuje, které dílčí nástroje použít. Další informace najdete v části dílčí sady nástrojů v [sada nástrojů (atribut ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).<br /><br /> Sada nástrojů obsahuje úkoly, cíle a nástroje, které slouží k sestavení aplikace. Mezi tyto nástroje patří kompilátory jako csc.exe a vbc.exe. Další informace o sady nástrojů najdete v tématu [sada nástrojů (atribut ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md), [standardní a vlastní konfigurace sady nástrojů](../msbuild/standard-and-custom-toolset-configurations.md), a [cílení na více verzí](../msbuild/msbuild-multitargeting-overview.md). **Poznámka:** verzi sady nástrojů není stejná jako cílový rámec, což je verze rozhraní .NET Framework, na kterém je projekt určený pro spuštění. Další informace najdete v tématu [Cílová architektura a cílová platforma](../msbuild/msbuild-target-framework-and-target-platform.md).|  
|/ validate: [`schema`]|/Val [`schema`]|Ověřit soubor projektu a, pokud je ověření úspěšné, sestavte projekt.<br /><br /> Pokud nezadáte `schema`, projekt bude ověřeno výchozí schéma.<br /><br /> Pokud zadáte `schema`, projekt se ověřit proti schématu, který zadáte.<br /><br /> Toto nastavení je příklad: `/validate:MyExtendedBuildSchema.xsd`|  
|/ verbosity:`level`|/ v:`level`|Určuje množství informací, které chcete zobrazit v protokolu sestavení. Každý protokolovač zobrazuje události na základě úrovně podrobností, které jste nastavili pro tento protokolovač.<br /><br /> Můžete zadat následující úrovně podrobností: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.<br /><br /> Toto nastavení je příklad: `/verbosity:quiet`|  
|/ Version|/ ver|Zobrazit informace o verzi. Projekt není sestaven.|  
|@`file`||Vložte přepínače příkazového řádku z textového souboru. Pokud máte více souborů, můžete je zadat samostatně. Další informace najdete v tématu [soubory odpovědí](../msbuild/msbuild-response-files.md).|  
  
### <a name="switches-for-loggers"></a>Přepínače protokolovacích nástrojů  
  
|Přepínač|Krátký tvar|Popis|  
|------------|----------------|-----------------|  
|/consoleloggerparameters:<br /><br /> `parameters`|/CLP:`parameters`|Předání parametrů, které určíte k protokolovací nástroj konzoly, která zobrazí informace o sestavení v okně konzoly. Můžete zadat následující parametry:<br /><br /> -   **PerformanceSummary**. Zobrazit čas strávený v úkoly, cíle a projekty.<br />-   **Souhrn**. Zobrazte souhrn upozornění a chyby na konci.<br />-   **NoSummary**. Nechcete zobrazit souhrn upozornění a chyby na konci.<br />-   **ErrorsOnly**. Zobrazit pouze chyby.<br />-   **WarningsOnly**. Zobrazit pouze upozornění.<br />-   **NoItemAndPropertyList**. Nezobrazovat seznam položek a vlastností, které se objeví na začátku každého sestavení projektu, pokud je nastavena úroveň podrobností `diagnostic`.<br />-   **ShowCommandLine**. Zobrazit `TaskCommandLineEvent` zprávy.<br />-   **ShowTimestamp**. Zobrazení časové razítko jako předpona pro všechny zprávy.<br />-   **ShowEventId**. Zobrazit ID události pro každou spuštěnou událost, dokončení události a zprávy.<br />-   **ForceNoAlign**. Není Zarovná text k velikost vyrovnávací paměti konzoly.<br />-   **DisableConsoleColor**. Použijte výchozí barvy konzoly pro všechny zprávy protokolování.<br />-   **DisableMPLogging**. Zakážete protokolování víceprocesorových styl výstupu při spuštění v režimu – s více procesory.<br />-   **EnableMPLogging**. Styl s více procesory protokolování povolte, i v případě, že je spuštěn v režimu – s více procesory. Tento styl protokolování je ve výchozím.<br />-   **Úroveň podrobností**. Přepsat **/verbosity** nastavení pro tento protokolovač.<br /><br /> K oddělení více parametrů, jak ukazuje následující příklad použijte středníky nebo čárkami:<br /><br /> `/consoleloggerparameters:PerformanceSummary;NoSummary /verbosity:minimal`|  
|/distributedFileLogger|/DFL|Do vlastního souboru protokolu výstupu sestavení každého uzlu MSBuild. Počáteční umístění těchto souborů je aktuální adresář. Ve výchozím nastavení, budou pojmenovány "MSBuild*NodeId*.log". Můžete použít **/fileLoggerParameters** přepínače a zadejte umístění souborů a dalších parametrů pro fileLogger.<br /><br /> Pokud název souboru protokolu s použitím **/fileLoggerParameters** přepínače, distribuovaného protokolovacího nástroje se použít název jako šablona a připojte ID uzlu na tento název při vytváření souboru protokolu pro každý uzel.|  
|/distributedlogger:<br /><br /> `central logger`*<br /><br /> `forwarding logger`|/DL:`central logger`*`forwarding logger`|Protokolování událostí z nástroje MSBuild, instanci a jiné protokolovacího nástroje připojení k jednotlivým uzlům. Pokud chcete zadat více Protokolovací nástroje, zadejte každou protokolovací nástroj zvlášť.<br /><br /> Použijte protokolovací nástroj syntaxi k určení protokolovací nástroj. Syntaxe protokolovací nástroj, najdete v článku **/logger** přepínač níže.<br /><br /> Následující příklady ukazují, jak použít tento přepínač:<br /><br /> `/dl:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `/dl:MyLogger,C:\My.dll*ForwardingLogger,C:\Logger.dll`|  
|/fileLogger<br /><br /> *[číslo]*|/fl[`number`]|Protokolovat výstup sestavení do jednoho souboru v aktuálním adresáři. Pokud nezadáte `number`, výstupní soubor má název msbuild.log. Pokud zadáte `number`, výstupní soubor má název msbuild`n`.log, kde n je `number`. `Number` může být číslo od 1 do 9.<br /><br /> Můžete použít **/fileLoggerParameters** přepínač k určení umístění souboru a další parametry fileLogger.|  
|/fileloggerparameters: [číslo]<br /><br /> `parameters`|/FLP: [ `number`] `parameters`|Určuje žádné další parametry pro soubor protokolovací nástroj a souborů DFS protokolovacího nástroje. Přítomnost tento přepínač vyplývá, že odpovídající /**filelogger [**`number`**]** přepínači je k dispozici. `Number` může být číslo od 1 do 9.<br /><br /> Můžete použít všechny parametry, které jsou uvedeny pro **/consoleloggerparameters**. Můžete také použít jeden nebo více z následujících parametrů:<br /><br /> -   **Soubor protokolu**. Cesta k souboru protokolu, do kterého se zapíše do protokolu sestavení. Protokolování souborů DFS předpon tuto cestu do názvy její soubory protokolu.<br />-   **Připojit**. Určuje, zda do protokolu sestavení je připojen k souboru protokolu, nebo ho přepíše. Když nastavíte přepínač, do protokolu sestavení je připojen k souboru protokolu. Pokud přepínač není k dispozici, jsou přepsány obsah k existujícímu souboru protokolu.<br />     Zadáte-li přidat přepínač, bez ohledu na to, zda je nastavena na hodnotu true nebo false, připojí se protokol. Pokud neuvedete přepínač připojit, v protokolu se přepíše.<br />     V tomto případě je přepsat soubor: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log`<br />     V tomto případě je připojen soubor: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log;append=true`<br />     V tomto případě je připojen soubor: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log;append=false`<br />-   **Kódování**. Určuje kódování souboru (například UTF-8, Unicode nebo ASCII).<br /><br /> Následující příklad generuje upozornění a chyby samostatné soubory protokolu:<br /><br /> `/flp1:logfile=errors.txt;errorsonly /flp2:logfile=warnings.txt;warningsonly`<br /><br /> Následující příklady ukazují další možnosti:<br /><br /> `/fileLoggerParameters:LogFile=MyLog.log;Append; Verbosity=diagnostic;Encoding=UTF-8`<br /><br /> `/flp:Summary;Verbosity=minimal;LogFile=msbuild.sum`<br /><br /> `/flp1:warningsonly;logfile=msbuild.wrn`<br /><br /> `/flp2:errorsonly;logfile=msbuild.err`|  
|/Logger:<br /><br /> `logger`|l:`logger`|Určuje protokolovací nástroj pro použití k protokolování událostí z nástroje MSBuild. Pokud chcete zadat více Protokolovací nástroje, zadejte každou protokolovací nástroj zvlášť.<br /><br /> Použijte následující syntaxi pro `logger`: `[``LoggerClass``,]``LoggerAssembly``[;``LoggerParameters``]`<br /><br /> Použijte následující syntaxi pro `LoggerClass`: `[``PartialOrFullNamespace``.]``LoggerClassName`<br /><br /> Nemusíte určovat třídu protokolovací nástroj, pokud obsahuje přesně jeden protokolovacího nástroje sestavení.<br /><br /> Použijte následující syntaxi pro `LoggerAssembly`: `{``AssemblyName``[,``StrongName``] &#124;` `AssemblyFile``}`<br /><br /> Protokolovací nástroj parametry jsou volitelné a jsou předány do protokolovacího nástroje přesně tak, jak je zadáte.<br /><br /> Následující příklady používají **/logger** přepnout.<br /><br /> `/logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `/logger:XMLLogger,C:\Loggers\MyLogger.dll;OutputAsHTML`|  
|/noconsolelogger|/noconlog|Zakázat výchozí protokolovací nástroj konzoly a není protokolování událostí do konzoly.|  
  
## <a name="example"></a>Příklad  
 Následující příklad je založen `rebuild` cíl `MyProject.proj` projektu.  
  
```  
MSBuild.exe MyProject.proj /t:rebuild  
```  
  
## <a name="example"></a>Příklad  
 MSBuild.exe můžete použít k provádění složitějších sestavení. Například můžete použít k sestavování specifických cílů konkrétní projekty v řešení. Následující příklad znovu sestaví projekt `NotInSolutionFolder` a vyčistí projektu `InSolutionFolder`, což je v `NewFolder` složku řešení.  
  
```  
msbuild SlnFolders.sln /t:NotInSolutionfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)   
 [Obecné vlastnosti projektu nástroje MSBuild](../msbuild/common-msbuild-project-properties.md)



