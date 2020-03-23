---
title: Odkaz na příkazový řádek MSBuild | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb95da599e6362ad32c0ef94dcf9c184269ddedf
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633405"
---
# <a name="msbuild-command-line-reference"></a>Odkaz na příkazový řádek MSBuild

Při použití *msbuild.exe* k vytvoření projektu nebo souboru řešení, můžete zahrnout několik přepínačů určit různé aspekty procesu.

Každý přepínač je k dispozici ve dvou formách: -switch a /switch. V dokumentaci se zobrazí pouze formulář -switch. Přepínače nerozlišují malá a velká písmena. Pokud spustíte MSBuild z jiného prostředí než příkazového řádku systému Windows, seznamy argumentů přepínače (oddělené středníky nebo čárky) může potřebovat jednoduché nebo dvojité uvozovky, aby bylo zajištěno, že seznamy jsou předány MSBuild namísto interpretován shell.

## <a name="syntax"></a>Syntaxe

```cmd
MSBuild.exe [Switches] [ProjectFile]
```

## <a name="arguments"></a>Argumenty

|Argument|Popis|
|--------------|-----------------|
|`ProjectFile`|Vytvoří cíle v souboru projektu, který zadáte. Pokud nezadáte soubor projektu, MSBuild vyhledá aktuální pracovní adresář pro příponu názvu souboru, která končí *v proj* a používá tento soubor. Můžete také zadat soubor řešení sady Visual Studio pro tento argument.|

## <a name="switches"></a>Přepínače

|Přepínač|Krátký tvar|Popis|
|------------|----------------|-----------------|
|-detailedSummary|-ds|Zobrazit podrobné informace na konci protokolu sestavení o konfiguracích, které byly vytvořeny a jak byly naplánovány na uzly.|
|-graphBuild[:`True` `False`nebo ]|-graf[:`True` `False`nebo ]|Způsobí, že MSBuild vytvořit a vytvořit graf projektu. Vytvoření grafu zahrnuje identifikaci odkazů na projekt tvořit závislosti. Vytvoření tohoto grafu zahrnuje pokus o vytvoření odkazy na projekt před projekty, které odkazují na ně, lišící se od tradiční ho plánování MSBuild.|
|-pomoc|/? nebo -h|Zobrazení informací o využití. Následující příkaz je příkladem:<br /><br /> `msbuild.exe -?`|
|-ignoreProjectExtensions:`extensions`|-ignorovat:`extensions`|Při určování souboru projektu, který má být sestavován, ignorujte zadané přípony. Použijte středník nebo čárku k oddělení více rozšíření, jak ukazuje následující příklad:<br /><br /> `-ignoreprojectextensions:.vcproj,.sln`|
|-interaktivní[:`True` `False`nebo ]|-|Označuje, že akce v sestavení mohou pracovat s uživatelem.  Nepoužívejte tento argument v automatizovaném scénáři, kde není očekávána interaktivita. Zadání -interactive je stejné jako zadání -interactive:true.  Pomocí parametru přepište hodnotu, která pochází ze souboru odpovědí.
|-isolateProjects[:`True` `False`nebo ]|-izolovat[:`True` nebo `False`]|Způsobí, že MSBuild k sestavení každého projektu v izolaci. Toto je více omezující režim MSBuild, protože vyžaduje, aby graf projektu být staticky zjistitelné v době vyhodnocení, ale může zlepšit plánování a snížit nároky na paměť při vytváření velké sady projektů.|
|-maxCpuCount[:`number`]|-m[:`number`]|Určuje maximální počet souběžných procesů, které mají být používány při vytváření. Pokud tento přepínač nezahrnete, výchozí hodnota je 1. Pokud tento přepínač zahrnete bez zadání hodnoty, msbuild bude používat až do počtu procesorů v počítači. Další informace naleznete [v tématu Vytváření více projektů paralelně](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).<br /><br /> Následující příklad instruuje MSBuild k sestavení pomocí tří procesů MSBuild, což umožňuje sestavení tří projektů současně:<br /><br /> `msbuild myproject.proj -maxcpucount:3`|
|-noAutomatická odezva|-noautorsp|Nezahrnujte automaticky žádné soubory *MSBuild.rsp.*|
|-nodeReuse:`value`|-nr:`value`|Povolte nebo zakažte opakované použití uzlů MSBuild. Můžete určit tyto hodnoty:<br /><br /> -   **Pravda**. Uzly zůstávají po dokončení sestavení tak, aby je mohla používat následná sestavení (výchozí).<br />-   **False**. Uzly nezůstanou po dokončení sestavení.<br /><br /> Uzel odpovídá projektu, který je spuštěn. Pokud zahrnete přepínač **-maxcpucount,** více uzlů lze spustit současně.|
|-nologo||Nezobrazujte spouštěcí banner ani zprávu o autorských právech.|
|<a name="preprocess"></a>-preprocess[:`filepath`]|-pp[:`filepath`]|Vytvořte jeden agregovaný soubor projektu tak, že vložíte všechny soubory, které by byly importovány během sestavení s jejich hranicemi označenými. Pomocí tohoto přepínače můžete snadněji určit, které soubory jsou importovány, odkud jsou soubory importovány a které soubory přispívají k sestavení. Při použití tohoto přepínače není vytvořen projekt.<br /><br /> Pokud zadáte `filepath`, agregovaný soubor projektu je výstup do souboru. V opačném případě se výstup zobrazí v okně konzoly.<br /><br /> Informace o použití `Import` prvku k vložení souboru projektu do jiného souboru projektu naleznete v [tématech Import elementu (MSBuild)](../msbuild/import-element-msbuild.md) a [Postup: Použijte stejný cíl ve více souborech projektu](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).|
|-outputResultsCache[:cacheFile]|-orc[:cacheFile]|Výstupní soubor mezipaměti, kde MSBuild bude psát obsah jeho mezipaměti výsledek sestavení na konci sestavení. Nastavení to také zapne izolované sestavení (-izolovat).|
|-profileHodnocení:`<file>`|-|Profily MSBuild hodnocení a zapíše výsledek do zadaného souboru. Pokud je přípona zadaného souboru '.md', výsledek je generován ve formátu Markdown. V opačném případě je vytvořen soubor oddělený tabulátory.|
|-majetek:`name`=`value`|-p:`name`=`value`|Nastavte nebo přepište zadané vlastnosti `name` na úrovni projektu, kde je název vlastnosti a `value` je hodnota vlastnosti. Zadejte každou vlastnost samostatně nebo použijte středník nebo čárku k oddělení více vlastností, jak ukazuje následující příklad:<br /><br /> `-property:WarningLevel=2;OutDir=bin\Debug`|
|-obnovit|-r|Spustí `Restore` cíl před sestavením skutečné cíle.|
|-restoreProperty:`name=value`|-rp:`name=value`|Nastavte nebo přepište tyto vlastnosti na úrovni projektu pouze během obnovení a nepoužívejte vlastnosti zadané s argumentem -property. `name`je název vlastnosti `value` a je hodnota vlastnosti. Pomocí středníku nebo čárky oddělte více vlastností nebo zadejte každou vlastnost zvlášť.|
|-cíl:`targets`|-t:`targets`|Sestavení zadané cíle v projektu. Zadejte každý cíl samostatně nebo použijte středník nebo čárku k oddělení více cílů, jak ukazuje následující příklad:<br /><br /> `-target:PrepareResources;Compile`<br /><br /> Pokud zadáte všechny cíle pomocí tohoto přepínače, jsou spuštěny namísto všech cílů v atributu `DefaultTargets` v souboru projektu. Další informace naleznete [v tématech Cílpořadí sestavení](../msbuild/target-build-order.md) a [Postup: Určete, který cíl má být sestavován jako první](../msbuild/how-to-specify-which-target-to-build-first.md).<br /><br /> Cíl je skupina úkolů. Další informace naleznete v tématu [Cíle](../msbuild/msbuild-targets.md).|
|-toolsVersion:`version`|-tv:`version`|Určuje verzi sady nástrojů, která má být používána k sestavení projektu, jak ukazuje následující příklad:`-toolsversion:3.5`<br /><br /> Pomocí tohoto přepínače můžete vytvořit projekt a zadat verzi, která se liší od verze, která je zadána v [elementu Project (MSBuild).](../msbuild/project-element-msbuild.md) Další informace naleznete [v tématu Overriding ToolsVersion settings](../msbuild/overriding-toolsversion-settings.md).<br /><br /> Pro MSBuild 4.5 můžete zadat následující `version`hodnoty pro : 2.0, 3.5 a 4.0. Pokud zadáte hodnotu `VisualStudioVersion` 4.0, vlastnost sestavení určí, kterou podsadu nástrojů chcete použít. Další informace naleznete v části Podsady nástrojů [sady nástrojů (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).<br /><br /> Sada nástrojů se skládá z úkolů, cílů a nástrojů, které se používají k vytvoření aplikace. Nástroje zahrnují kompilátory, například *csc.exe* a *vbc.exe*. Další informace o sadách nástrojů naleznete v [tématech Sada nástrojů (ToolsVersion),](../msbuild/msbuild-toolset-toolsversion.md) [Standardní a vlastní konfigurace sad nástrojů](../msbuild/standard-and-custom-toolset-configurations.md)a [Multitargeting](../msbuild/msbuild-multitargeting-overview.md). **Poznámka:**  Verze sady nástrojů není stejná jako cílový rámec, což je verze rozhraní .NET Framework, na kterém je projekt vytvořen ke spuštění. Další informace naleznete v tématu [Target framework a target platform .](../msbuild/msbuild-target-framework-and-target-platform.md)|
|-ověřit:[`schema`]|-val[`schema`]|Ověřte soubor projektu a pokud je ověření úspěšné, vytvořte projekt.<br /><br /> Pokud nezadáte `schema`, projekt je ověřen proti výchozí schéma.<br /><br /> Pokud zadáte `schema`, projekt je ověřen proti zadané schéma.<br /><br /> Následující nastavení je příkladem:`-validate:MyExtendedBuildSchema.xsd`|
|-podrobnost:`level`|-v:`level`|Určuje množství informací, které se mají zobrazit v protokolu sestavení. Každý protokolovací protokol zobrazuje události na základě úrovně podrobností, které jste nastavili pro tento protokolovací nástroj.<br /><br /> Můžete určit následující úrovně podrobností: `q[uiet]` `m[inimal]`, `n[ormal]` , `d[etailed]`(výchozí), a `diag[nostic]`.<br /><br /> Následující nastavení je příkladem:`-verbosity:quiet`
|-verze|-ver|Zobrazit pouze informace o verzi. Projekt není sestaven.|
|@`file`||Vložte přepínače příkazového řádku z textového souboru. Pokud máte více souborů, zadejte je samostatně. Další informace naleznete v [tématu Response files](../msbuild/msbuild-response-files.md).|
|-warnAsError[:`code``;code2`[ ]|-err[`:code``;code2`[ ]|Seznam kódů upozornění, které mají být považovány za chyby.  K oddělení více výstražných kódů použijte středník nebo čárku. Chcete-li považovat všechna upozornění za chyby, použijte přepínač bez hodnot. Pokud je upozornění považováno za chybu, cíl pokračuje v provádění, jako by se jednalo o upozornění, ale celkové sestavení se nezdaří.<br/><br/>Příklad: `-err:MSB4130`|
|-warnAsMessage[:`code``;code2`[ ]|-noWarn[:`code``;code2`[ ]|Seznam varovných kódů pro považovány za zprávy s nízkou důležitostí.  K oddělení více výstražných kódů použijte středník nebo čárku.<br/><br/>Příklad: `-noWarn:MSB3026`|

### <a name="switches-for-loggers"></a>Přepínače pro úhozy kláves

|Přepínač|Krátký tvar|Popis|
|------------|----------------|-----------------|
|-binaryLogger[:[LogFile=]`output.binlog`<br/>[; ProjectImports=[Žádný,Vložit,ZipFile]]]|-bl|Serializuje všechny události sestavení do komprimovaného binárního souboru. Ve výchozím nastavení je soubor v aktuálním adresáři s názvem *msbuild.binlog*. Binární protokol je podrobný popis procesu sestavení, který lze později použít k rekonstrukci textových protokolů a použít jinými analytickými nástroji. Binární protokol je obvykle 10-20x menší než nejpodrobnější protokol na úrovni diagnostiky textu, ale obsahuje další informace.<br /><br />Binární protokolování ve výchozím nastavení shromažďuje zdrojový text souborů projektu, včetně všech importovaných projektů a cílových souborů, ke kterým došlo během sestavení. Volitelný `ProjectImports` přepínač řídí toto chování:<br /><br /> -   **ProjectImports=Žádný**. Neshromažďujte importy projektu.<br /> -   **ProjectImports=Vložit**. Vložit importy projektu do souboru protokolu (výchozí).<br /> -   **ProjectImports=ZipFile**. Uložte soubory projektu na \< * \<výstup>.projectimports.zip,* kde výstup> je stejný název jako název binárního souboru protokolu.<br /><br />Výchozí nastavení pro ProjectImports je Vložit.<br />**Poznámka:** protokolovací nástroj neshromažďuje zdrojové soubory, které nejsou msbuild, jako jsou *.cs*, *Cpp* atd.<br />Soubor *.binlog* lze "přehrát" předáním *msbuild.exe* jako argument namísto projektu/řešení. Ostatní úhozy kláves obdrží informace obsažené v souboru protokolu, jako by se dělo původní sestavení. Můžete si přečíst více o binární log a jeho použití na adrese:https://github.com/Microsoft/msbuild/wiki/Binary-Log <br /><br />**Příklady**:<br /> -   `-bl`<br /> -    `-bl:output.binlog`<br /> -   `-bl:output.binlog;ProjectImports=None`<br /> -   `-bl:output.binlog;ProjectImports=ZipFile`<br /> -   `-bl:..\..\custom.binlog`<br /> -   `-binaryLogger`|
|-consoleLoggerParameters:<br /><br /> `parameters`|-clp:`parameters`|Předajte parametry, které zadáte, do protokolování konzoly, který zobrazuje informace o sestavení v okně konzoly. Můžete zadat následující parametry:<br /><br /> -   **PerformanceSummary**. Zobrazit čas strávený v úkolech, cílech a projektech.<br />-   **Shrnutí**. Zobrazí souhrn chyby a upozornění na konci.<br />-   **NoSummary**. Nezobrazovat souhrn chyb y a upozornění na konci.<br />-   **Pouze chyby**. Zobrazit pouze chyby.<br />-   **WarningsOnly**. Zobrazit pouze varování.<br />-   **NoItemandPropertyList**. Nezobrazovat seznam položek a vlastností, které by se zobrazí na začátku každého sestavení `diagnostic`projektu, pokud je nastavena úroveň podrobností na .<br />-   **Zobrazitpříkazová čára**. Zobrazit `TaskCommandLineEvent` zprávy.<br />-   **ZobrazitTimerazítko**. Zobrazí časové razítko jako předponu k libovolné zprávě.<br />-   **ShowEventId**. Zobrazí ID události pro každou zahájenou událost, dokončenou událost a zprávu.<br />-   **ForceNoAlign**. Nezarovnávejte text s velikostí vyrovnávací paměti konzoly.<br />-   **Zakázat ConsoleColor**. Pro všechny zprávy protokolování použijte výchozí barvy konzoly.<br />-   **Zakázat protokolOVÁNÍ mpů**. Zakažte styl víceprocesorového protokolování výstupu při spuštění v režimu bez více procesorů.<br />-   **EnableMPLogging**. Povolte styl protokolování s více procesory i při spuštění v režimu bez více procesorů. Tento styl protokolování je ve výchozím nastavení zapnutý.<br />-   **Výmluvnost**. Přepsat **-podrobnost** nastavení pro tento protokolovací nástroj.<br /><br /> Pomocí středníku oddělte více parametrů, jak ukazuje následující příklad:<br /><br /> `-consoleloggerparameters:PerformanceSummary;NoSummary -verbosity:minimal`<br/><br/> Výchozí protokolování konzoly je na normální `Summary`podrobnost a obsahuje .|
|-distributedFileLogger|-dfl|Protokolujte výstup sestavení každého uzlu MSBuild do vlastního souboru. Počáteční umístění těchto souborů je aktuální adresář. Ve výchozím nastavení se soubory nazývají *MSBuild\<NodeId>.log*. Přepínač **-fileLoggerParameters** můžete použít k určení umístění souborů a dalších parametrů fileLoggeru.<br /><br /> Pokud pojmenujete soubor protokolu pomocí přepínače **-fileLoggerParameters,** distribuovaný záznamník použije tento název jako šablonu a připojí ID uzlu k tomuto názvu při vytváření souboru protokolu pro každý uzel.|
|-distributedLogger:<br /><br /> `central logger`*<br /><br /> `forwarding logger`|-dl:`central logger`*`forwarding logger`|Protokolovat události z MSBuild, připojení jiné instance protokolování do každého uzlu. Chcete-li zadat více úhozů kláves, zadejte každý protokolování samostatně.<br /><br /> Syntaxe protokolování slouží k určení protokolování. Syntaxe protokolování naleznete v přepínači **-logger** níže.<br /><br /> Následující příklady ukazují, jak používat tento přepínač:<br /><br /> `-dl:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `-dl:MyLogger,C:\My.dll*ForwardingLogger,C:\Logger.dll`|
|-fileLogger<br /><br /> *[číslo]*|-fl[`number`]|Protokolujte výstup sestavení do jednoho souboru v aktuálním adresáři. Pokud nezadáte `number`, bude výstupní soubor pojmenován *msbuild.log*. Pokud zadáte `number`, bude výstupní soubor pojmenován *msbuild\<n>.log*, kde \<n> je `number`. `Number`může být číslice od 1 do 9.<br /><br /> Přepínač **-fileLoggerParameters** můžete použít k určení umístění souboru a dalších parametrů fileLoggeru.|
|-fileLoggerParameters:[číslo]<br /><br /> `parameters`|-flp:[ `number`]`parameters`|Určuje všechny další parametry pro záznamník souborů a distribuovaný soubor logger. Přítomnost tohoto přepínače znamená, že je přítomen odpovídající přepínač -**filelogger[**`number`**]** `Number`může být číslice od 1 do 9.<br /><br /> Můžete použít všechny parametry, které jsou uvedeny pro **parametry -consoleloggerparameters**. Můžete také použít jeden nebo více z následujících parametrů:<br /><br /> -   **Soubor protokolu**. Cesta k souboru protokolu, do kterého je zapsán protokol sestavení. Distribuovaný záznamník souborů předponu tuto cestu k názvům svých souborů protokolu.<br />-   **Připojit**. Určuje, zda je protokol sestavení připojen k souboru protokolu nebo jej přepíše. Když nastavíte přepínač, protokol sestavení je připojen k souboru protokolu. Pokud přepínač není k dispozici, obsah existujícího souboru protokolu jsou přepsány.<br />     Pokud zahrnete přepínač připojení, bez ohledu na to, zda je nastavena na hodnotu true nebo false, protokol je připojen. Pokud nezahrnete přepínač připojení, protokol se přepíše.<br />     V tomto případě je soubor přepsán:`msbuild myfile.proj -l:FileLogger,Microsoft.Build;logfile=MyLog.log`<br />     V tomto případě je soubor připojen:`msbuild myfile.proj -l:FileLogger,Microsoft.Build;logfile=MyLog.log;append=true`<br />     V tomto případě je soubor připojen:`msbuild myfile.proj -l:FileLogger,Microsoft.Build;logfile=MyLog.log;append=false`<br />-   **Kódování**. Určuje kódování souboru (například UTF-8, Unicode nebo ASCII).<br /><br /> Následující příklad generuje samostatné soubory protokolu pro upozornění a chyby:<br /><br /> `-flp1:logfile=errors.txt;errorsonly -flp2:logfile=warnings.txt;warningsonly`<br /><br /> Následující příklady ukazují další možnosti:<br /><br /> `-fileLoggerParameters:LogFile=MyLog.log;Append; Verbosity=diagnostic;Encoding=UTF-8`<br /><br /> `-flp:Summary;Verbosity=minimal;LogFile=msbuild.sum`<br /><br /> `-flp1:warningsonly;logfile=msbuild.wrn`<br /><br /> `-flp2:errorsonly;logfile=msbuild.err`|
|-logger:<br /><br /> `logger`|-l:`logger`|Určuje protokolovací nástroj, který má být používán k protokolování událostí z nástroje MSBuild. Chcete-li zadat více úhozů kláves, zadejte každý protokolování samostatně.<br /><br /> Použijte následující syntaxi pro `logger`:`[``LoggerClass``,]``LoggerAssembly``[;``LoggerParameters``]`<br /><br /> Použijte následující syntaxi pro `LoggerClass`:`[``PartialOrFullNamespace``.]``LoggerClassName`<br /><br /> Není nutné zadat logger třídy, pokud sestavení obsahuje přesně jeden protokolovací nástroj.<br /><br /> Použijte následující syntaxi pro `LoggerAssembly`: `{``AssemblyName``[,``StrongName``] &#124;``AssemblyFile``}`<br /><br /> Parametry protokolování jsou volitelné a jsou předány do loggeru přesně tak, jak je zadáte.<br /><br /> Následující příklady používají přepínač **-logger.**<br /><br /> `-logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `-logger:XMLLogger,C:\Loggers\MyLogger.dll;OutputAsHTML`|
|-noConsoleLogger|-noconlog|Zakažte výchozí protokolování konzoly a nezasílejte události do konzoly.|

## <a name="example"></a>Příklad

 Následující příklad vytvoří `rebuild` cíl projektu *MyProject.proj.*

```cmd
MSBuild.exe MyProject.proj -t:rebuild
```

## <a name="example"></a>Příklad

 *MSBuild.exe* můžete použít k provedení složitější sestavení. Můžete ji například použít k vytvoření konkrétních cílů konkrétních projektů v řešení. Následující příklad znovu vytvoří `NotInSolutionFolder` projekt a `InSolutionFolder`vyčistí projekt , který je ve složce řešení *NewFolder.*

```cmd
msbuild SlnFolders.sln -t:NotInSolutionfolder:Rebuild;NewFolder\InSolutionFolder:Clean
```

## <a name="see-also"></a>Viz také

- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
- [Běžné vlastnosti projektu MSBuild](../msbuild/common-msbuild-project-properties.md)
