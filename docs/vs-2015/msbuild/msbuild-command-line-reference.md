---
title: Reference k příkazovému řádku nástroje MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: 8d40bfefb1f89496b538612dfa1819cc6d65c76c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181053"
---
# <a name="msbuild-command-line-reference"></a>Referenční dokumentace pro použití nástroje MSBuild v příkazovém řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při použití MSBuild.exe k sestavení projektu nebo souboru řešení můžete zahrnout několik přepínačů pro určení různých aspektů procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
MSBuild.exe [Switches] [ProjectFile]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Argument|Popis|  
|--------------|-----------------|  
|`ProjectFile`|Vytvoří cíle v souboru projektu, který zadáte. Pokud nezadáte soubor projektu, nástroj MSBuild vyhledá v aktuálním pracovním adresáři příponu názvu souboru, která končí řetězcem "proj" a použije tento soubor. Můžete také zadat soubor řešení sady Visual Studio pro tento argument.|  
  
## <a name="switches"></a>Přepínače  
  
|Přepínač|Krátký tvar|Popis|  
|------------|----------------|-----------------|  
|/help|/? nebo/h|Zobrazit informace o použití. Následující příkaz je příkladem:<br /><br /> `msbuild.exe /?`|  
|/detailedsummary|/ds|Zobrazit podrobné informace na konci protokolu sestavení o konfiguracích, které byly vytvořeny a jak byly naplánovány na uzly.|  
|/ignoreprojectextensions: `extensions`|/Ignore `extensions`|Ignorovat zadaná rozšíření při určování, který soubor projektu se má sestavit. Použijte středník nebo čárku pro oddělení více rozšíření, jak ukazuje následující příklad:<br /><br /> `/ignoreprojectextensions:.vcproj,.sln`|  
|/maxcpucount [: `number` ]|/m [: `number` ]|Určuje maximální počet souběžných procesů, které mají být použity při sestavování. Pokud tento přepínač nezadáte, výchozí hodnota je 1. Pokud tento přepínač zadáte bez zadání hodnoty, nástroj MSBuild použije množství procesorů v počítači. Další informace naleznete v tématu [Souběžné sestavování více projektů](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).<br /><br /> Následující příklad instruuje nástroj MSBuild k sestavení pomocí tří procesů MSBuild, které umožňují sestavovat tři projekty ve stejnou dobu:<br /><br /> `msbuild myproject.proj /maxcpucount:3`|  
|/noautoresponse|/noautorsp|Nezahrnujte žádné soubory MSBuild. rsp automaticky.|  
|/nodeReuse:`value`|/Nr`value`|Povolí nebo zakáže opakované použití uzlů MSBuild. Můžete určit tyto hodnoty:<br /><br /> -   **Hodnota true**. Uzly zůstanou po dokončení sestavení, aby je mohli použít následné sestavení (výchozí).<br />-   **Hodnota false**. Uzly po dokončení sestavení nezůstanou.<br /><br /> Uzel odpovídá projektu, který je spuštěn. Pokud zahrnete přepínač **/maxcpucount** , může být souběžně spuštěno více uzlů.|  
|/nologo||Nezobrazovat úvodní nápis nebo zprávu o autorských právech.|  
|/preprocess [: `filepath` ]|/PP [: `filepath` ]|Vytvořte jeden agregovaný soubor projektu tak, že zapíšete všechny soubory, které by se importovaly během sestavení, se svými hranicemi označenými. Pomocí tohoto přepínače můžete snadněji určit, které soubory se importují, odkud se soubory importují a které soubory přispívají k sestavení. Když použijete tento přepínač, projekt není sestaven.<br /><br /> Pokud zadáte `filepath` , agregovaný soubor projektu je výstupem do souboru. V opačném případě se výstup zobrazí v okně konzoly.<br /><br /> Informace o tom, jak použít `Import` element pro vložení souboru projektu do jiného souboru projektu, naleznete v tématu [Import element (MSBuild)](../msbuild/import-element-msbuild.md) a [How to: použijte stejný cíl ve více souborech projektu](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).|  
|majetek`name`=`value`|/p`name`=`value`|Nastaví nebo přepíše zadané vlastnosti na úrovni projektu, kde `name` je název vlastnosti a `value` je hodnotou vlastnosti. Jednotlivé vlastnosti zadejte samostatně nebo použijte středník nebo čárku pro oddělení více vlastností, jak ukazuje následující příklad:<br /><br /> `/property:WarningLevel=2;OutDir=bin\Debug`|  
|/Target`targets`|parametr`targets`|Sestavte zadané cíle v projektu. Určete každý cíl samostatně nebo použijte středník nebo čárku pro oddělení více cílů, jak ukazuje následující příklad:<br /><br /> `/target:Resources;Compile`<br /><br /> Pokud zadáte všechny cíle pomocí tohoto přepínače, jsou spuštěny namísto všech cílů v `DefaultTargets` atributu v souboru projektu. Další informace naleznete v tématu [cílové pořadí sestavení](../msbuild/target-build-order.md) a [Postup: určení cíle, který se má sestavit jako první](../msbuild/how-to-specify-which-target-to-build-first.md).<br /><br /> Cíl je skupina úkolů. Další informace najdete v tématu [cíle](../msbuild/msbuild-targets.md).|  
|ToolsVersion`version`|řadu`version`|Určuje verzi sady nástrojů, která se má použít k sestavení projektu, jak ukazuje následující příklad: `/toolsversion:3.5`<br /><br /> Pomocí tohoto přepínače můžete sestavit projekt a zadat verzi, která se liší od verze, která je zadána v [elementu projektu (MSBuild)](../msbuild/project-element-msbuild.md). Další informace najdete v tématu [přepsání nastavení ToolsVersion](../msbuild/overriding-toolsversion-settings.md).<br /><br /> Pro MSBuild 4,5 můžete zadat následující hodnoty pro `version` : 2,0, 3,5 a 4,0. Zadáte-li 4,0, `VisualStudioVersion` vlastnost Build určuje, kterou dílčí sadu nástrojů použít. Další informace naleznete v části sady [nástrojů sady nástrojů (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)dílčích sad nástrojů.<br /><br /> Sada nástrojů se skládá z úloh, cílů a nástrojů, které se používají k sestavení aplikace. Mezi tyto nástroje patří kompilátory, jako jsou csc.exe a vbc.exe. Další informace o sadě nástrojů naleznete v tématech [Sada nástrojů (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md), [standardní a vlastní konfigurace sady nástrojů](../msbuild/standard-and-custom-toolset-configurations.md)a [cílení](../msbuild/msbuild-multitargeting-overview.md)na více verzí. **Poznámka:**  Verze sady nástrojů není shodná s cílovou architekturou, což je verze .NET Framework, na které je projekt sestaven pro spuštění. Další informace naleznete v tématu [Cílová architektura a cílová platforma](../msbuild/msbuild-target-framework-and-target-platform.md).|  
|/Validate: [ `schema` ]|/Val [ `schema` ]|Ověřte soubor projektu a, pokud je ověření úspěšné, sestavte projekt.<br /><br /> Pokud nezadáte `schema` , projekt je ověřen proti výchozímu schématu.<br /><br /> Pokud zadáte `schema` , projekt se ověří podle schématu, které zadáte.<br /><br /> Toto nastavení je příklad: `/validate:MyExtendedBuildSchema.xsd`|  
|/Verbosity`level`|/v`level`|Určuje množství informací, které se mají zobrazit v protokolu sestavení. Každý protokolovací nástroj zobrazuje události na základě úrovně podrobností, kterou jste nastavili pro daný protokolovací nástroj.<br /><br /> Můžete zadat následující úrovně podrobností: `q[uiet]` , `m[inimal]` , `n[ormal]` , `d[etailed]` a `diag[nostic]` .<br /><br /> Toto nastavení je příklad: `/verbosity:quiet`|  
|/Version|/ver|Zobrazí pouze informace o verzi. Projekt není sestaven.|  
|@`file`||Vloží přepínače příkazového řádku z textového souboru. Pokud máte více souborů, zadejte je samostatně. Další informace najdete v tématu [soubory odezvy](../msbuild/msbuild-response-files.md).|  
  
### <a name="switches-for-loggers"></a>Přepínače protokolovacích nástrojů  
  
|Přepínač|Krátký tvar|Popis|  
|------------|----------------|-----------------|  
|/consoleloggerparameters:<br /><br /> `parameters`|/clp:`parameters`|Předejte parametry, které zadáte, do protokolovacího nástroje konzoly, který zobrazí informace o sestavení v okně konzoly. Můžete zadat následující parametry:<br /><br /> -   **PerformanceSummary**. Zobrazuje čas strávený v úkolech, cílech a projektech.<br />-   **Souhrn**. Zobrazit souhrn chyb a upozornění na konci.<br />-   **Souhrn**. Nezobrazovat chyby a souhrn upozornění na konci.<br />-   **ErrorsOnly**. Zobrazit pouze chyby.<br />-   **WarningsOnly**. Zobrazit pouze upozornění.<br />-   **NoItemAndPropertyList**. Nezobrazovat seznam položek a vlastností, které by se zobrazily na začátku každého sestavení projektu, pokud je úroveň podrobností nastavená na `diagnostic` .<br />-   **ShowCommandLine**. Zobrazit `TaskCommandLineEvent` zprávy.<br />-   **ShowTimestamp**. Zobrazit časové razítko jako předponu libovolné zprávy<br />-   **ShowEventId**. Zobrazí ID události pro každou spuštěnou událost, dokončenou událost a zprávu.<br />-   **ForceNoAlign**. Nesjednotit text na velikost vyrovnávací paměti konzoly.<br />-   **DisableConsoleColor**. Pro všechny zprávy protokolu použijte výchozí barvy konzoly.<br />-   **DisableMPLogging**. Při spuštění v režimu bez více procesorů zakažte styl protokolování s více procesory.<br />-   **EnableMPLogging**. Povolte styl protokolování s více procesory i v případě, že je spuštěný v režimu bez více procesorů. Tento styl protokolování je ve výchozím nastavení zapnutý.<br />-   **Podrobnosti**. Přepsat nastavení **/Verbosity** pro tento protokolovací nástroj<br /><br /> Použijte středník nebo čárku pro oddělení více parametrů, jak ukazuje následující příklad:<br /><br /> `/consoleloggerparameters:PerformanceSummary;NoSummary /verbosity:minimal`|  
|/distributedFileLogger|/dfl|Zaprotokoluje výstup sestavení každého uzlu MSBuild do vlastního souboru. Výchozí umístění těchto souborů je aktuální adresář. Ve výchozím nastavení jsou soubory pojmenovány "MSBuild*NodeId*. log". Pomocí přepínače **/fileLoggerParameters** můžete zadat umístění souborů a dalších parametrů pro protokolovací nástroj.<br /><br /> Pokud zadáte název souboru protokolu pomocí přepínače **/fileLoggerParameters** , distribuovaný protokolovací nástroj použije tento název jako šablonu a při vytváření souboru protokolu pro každý uzel připojí ID uzlu k tomuto názvu.|  
|/distributedlogger:<br /><br /> `central logger`*<br /><br /> `forwarding logger`|distribučního seznamu`central logger`*`forwarding logger`|Protokolujte události z nástroje MSBuild, připojíte k jednotlivým uzlům jinou instanci protokolovacího nástroje. Chcete-li zadat více protokolovacích nástrojů, zadejte jednotlivé protokolovací nástroje samostatně.<br /><br /> K určení protokolovacího nástroje slouží syntaxe protokolovacího nástroje. Syntaxi protokolovacího nástroje najdete níže v níže uvedeném přepínači **/Logger** .<br /><br /> Následující příklady ukazují, jak používat tento přepínač:<br /><br /> `/dl:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `/dl:MyLogger,C:\My.dll*ForwardingLogger,C:\Logger.dll`|  
|/fileLogger<br /><br /> *Automatické*|/FL [ `number` ]|Zaprotokoluje výstup sestavení do jednoho souboru v aktuálním adresáři. Pokud nezadáte `number` , výstupní soubor se jmenuje MSBuild. log. Pokud zadáte `number` , výstupní soubor se jmenuje MSBuild `n` . log, kde n je `number` . `Number` může to být číslice od 1 do 9.<br /><br /> Pomocí přepínače **/fileLoggerParameters** můžete zadat umístění souboru a dalších parametrů pro protokolovací nástroj.|  
|/fileLoggerParameters: [číslo]<br /><br /> `parameters`|/FLP: [ `number` ] `parameters`|Určuje všechny další parametry pro protokolovací nástroj souborů a protokolování distribuovaných souborů. Přítomnost tohoto přepínače znamená, že je k dispozici odpovídající přepínač/protokolovací nástroj **[** `number` **]** . `Number` může to být číslice od 1 do 9.<br /><br /> Můžete použít všechny parametry, které jsou uvedeny pro **/consoleloggerparameters**. Můžete také použít jeden nebo více z následujících parametrů:<br /><br /> -   **Soubor protokolu**. Cesta k souboru protokolu, do nějž je zapsán protokol sestavení. Protokolovací nástroj distribuovaného souboru přihlašuje tuto cestu k názvům jeho souborů protokolu.<br />-   **Připojit**. Určuje, zda je protokol sestavení připojen k souboru protokolu nebo Přepisuje. Při nastavení přepínače je protokol sestavení připojen do souboru protokolu. Pokud tento přepínač není k dispozici, obsah stávajícího souboru protokolu bude přepsán.<br />     Pokud vložíte přepínač připojit bez ohledu na to, zda je nastaven na hodnotu true nebo false, protokol bude připojen. Pokud nezahrnete přepínač Append, protokol se přepíše.<br />     V tomto případě je soubor přepsán: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log`<br />     V takovém případě je soubor připojen: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log;append=true`<br />     V takovém případě je soubor připojen: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log;append=false`<br />-   **Kódování**. Určuje kódování souboru (například UTF-8, Unicode nebo ASCII).<br /><br /> Následující příklad generuje samostatné soubory protokolu pro upozornění a chyby:<br /><br /> `/flp1:logfile=errors.txt;errorsonly /flp2:logfile=warnings.txt;warningsonly`<br /><br /> Následující příklady ukazují další možnosti:<br /><br /> `/fileLoggerParameters:LogFile=MyLog.log;Append; Verbosity=diagnostic;Encoding=UTF-8`<br /><br /> `/flp:Summary;Verbosity=minimal;LogFile=msbuild.sum`<br /><br /> `/flp1:warningsonly;logfile=msbuild.wrn`<br /><br /> `/flp2:errorsonly;logfile=msbuild.err`|  
|Nástroj<br /><br /> `logger`|/l`logger`|Určuje protokolovací nástroj, který se má použít k protokolování událostí z MSBuild. Chcete-li zadat více protokolovacích nástrojů, zadejte jednotlivé protokolovací nástroje samostatně.<br /><br /> Použijte následující syntaxi pro `logger` : `[``LoggerClass``,]``LoggerAssembly``[;``LoggerParameters``]`<br /><br /> Použijte následující syntaxi pro `LoggerClass` : `[``PartialOrFullNamespace``.]``LoggerClassName`<br /><br /> Není nutné určovat třídu protokolovacího nástroje, pokud sestavení obsahuje právě jeden protokolovací nástroj.<br /><br /> Použijte následující syntaxi pro `LoggerAssembly` : `{``AssemblyName``[,``StrongName``] &#124;``AssemblyFile``}`<br /><br /> Parametry protokolovacího nástroje jsou volitelné a jsou předány do protokolovacího nástroje přesně tak, jak je zadáte.<br /><br /> V následujících příkladech je použit přepínač **/Logger** .<br /><br /> `/logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `/logger:XMLLogger,C:\Loggers\MyLogger.dll;OutputAsHTML`|  
|/noconsolelogger|/noconlog|Zakáže výchozí protokolovací nástroj konzoly a neprotokoluje události do konzoly.|  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří `rebuild` cíl `MyProject.proj` projektu.  
  
```  
MSBuild.exe MyProject.proj /t:rebuild  
```  
  
## <a name="example"></a>Příklad  
 K provádění složitějších sestavení můžete použít MSBuild.exe. Můžete ho například použít k sestavení specifických cílů konkrétního projektu v řešení. Následující příklad znovu sestaví projekt `NotInSolutionFolder` a vyčistí projekt `InSolutionFolder` , který je ve `NewFolder` složce řešení.  
  
```  
msbuild SlnFolders.sln /t:NotInSolutionfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)   
 [Obecné vlastnosti projektu nástroje MSBuild](../msbuild/common-msbuild-project-properties.md)
