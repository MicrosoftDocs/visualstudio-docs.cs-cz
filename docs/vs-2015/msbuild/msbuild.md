---
title: MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, about MSBuild
- MSBuild, overview
ms.assetid: e39f13f7-1e1d-4435-95ca-0c222bca071c
caps.latest.revision: 62
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7ac637c478b5bb105b48abeb1d0ec074122e3dda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68739693"
---
# <a name="msbuild"></a>MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)]Je platforma pro vytváření aplikací. Tento modul, který je také známý jako MSBuild, poskytuje schéma XML pro soubor projektu, který určuje, jak platforma sestavení zpracovává a sestavuje software. Visual Studio používá MSBuild, ale nezávisí na aplikaci Visual Studio. Vyvoláním msbuild.exe v souboru projektu nebo řešení můžete orchestrovat a sestavovat produkty v prostředích, kde není nainstalována aplikace Visual Studio.  
  
 Visual Studio používá MSBuild k načtení a sestavení spravovaných projektů. Soubory projektu v aplikaci Visual Studio (. csproj, vbproj, vcxproj a jiné) obsahují kód XML nástroje MSBuild, který se spouští při vytváření projektu pomocí integrovaného vývojového prostředí (IDE). Projekty sady Visual Studio importují veškerá potřebná nastavení a procesy sestavení pro provádění typických vývojových prací, ale můžete je roztáhnout nebo upravit v rámci sady Visual Studio nebo pomocí editoru XML.  
  
 Informace o nástroji MSBuild pro jazyk C++ naleznete v tématu [MSBuild (Visual C++)](https://msdn.microsoft.com/library/7a1be7ff-0312-4669-adf2-5f5bf507d560).  
  
 Následující příklady ilustrují, kdy můžete spustit sestavení pomocí příkazového řádku MSBuild namísto integrovaného vývojového prostředí (IDE) sady Visual Studio.  
  
- Visual Studio není nainstalované.  
  
- Chcete použít 64 verzi nástroje MSBuild. Tato verze nástroje MSBuild je obvykle zbytečná, ale umožňuje nástroji MSBuild získat přístup k více paměti.  
  
- Chcete spustit sestavení ve více procesech. Můžete však použít rozhraní IDE k dosažení stejného výsledku pro projekty v jazyce C++ a C#.  
  
- Chcete upravit systém sestavení. Například může být vhodné povolit následující akce:  
  
  - Předzpracovat soubory před tím, než dosáhnou kompilátoru.  
  
  - Zkopírujte výstupy sestavení na jiné místo.  
  
  - Vytvoří komprimované soubory z výstupů sestavení.  
  
  - Proveďte krok po zpracování. Například může být vhodné razítko sestavení s jinou verzí.  
  
  Můžete napsat kód v integrovaném vývojovém prostředí sady Visual Studio, ale spustit sestavení pomocí nástroje MSBuild. Jako další alternativu můžete vytvořit kód v INTEGROVANÉm vývojovém počítači, ale pomocí příkazového řádku MSBuild sestavit kód, který je integrován od více vývojářů.  
  
> [!NOTE]
> Team Foundation Build můžete použít k automatické kompilaci, testování a nasazení vaší aplikace. Systém sestavení může automaticky spouštět sestavení při vrácení kódu se změnami vývojáři (například jako součást strategie průběžné integrace) nebo podle plánu (například sestavení testu na noční sestavení pro ověření). Sestavení Team Foundation zkompiluje váš kód pomocí nástroje MSBuild. Další informace naleznete v tématu [sestavování aplikace](/azure/devops/pipelines/index).  
  
 Toto téma poskytuje přehled nástroje MSBuild. Úvodní kurz najdete v tématu [Návod: použití nástroje MSBuild](../msbuild/walkthrough-using-msbuild.md).  
  
 **V tomto tématu**  
  
- [Použití nástroje MSBuild v příkazovém řádku](#BKMK_CommandPrompt)  
  
- [Soubor projektu](#BKMK_ProjectFile)  
  
  - [Vlastnosti](#BKMK_Properties)  

  - [Položky](#BKMK_Items)  

  - [Úlohy](#BKMK_Tasks)  

  - [Targets](#BKMK_Targets)  

- [Protokoly sestavení](#BKMK_BuildLogs)  
  
- [Použití nástroje MSBuild v aplikaci Visual Studio](#BKMK_VisualStudio)  
  
- [Cílení na více verzí](#BKMK_Multitargeting)  
  
## <a name="using-msbuild-at-a-command-prompt"></a><a name="BKMK_CommandPrompt"></a> Použití nástroje MSBuild v příkazovém řádku  
 Chcete-li spustit [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] příkaz na příkazovém řádku, předejte soubor projektu MSBuild.exe společně s příslušnými možnostmi příkazového řádku. Možnosti příkazového řádku umožňují nastavit vlastnosti, spustit konkrétní cíle a nastavit další možnosti, které řídí proces sestavení. Například použijte následující syntaxi příkazového řádku k sestavení souboru `MyProj.proj` s `Configuration` vlastností nastavenou na `Debug` .  
  
```  
MSBuild.exe MyProj.proj /property:Configuration=Debug  
```  
  
 Další informace o [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] možnostech příkazového řádku naleznete v tématu [Reference k příkazovému řádku](../msbuild/msbuild-command-line-reference.md).  
  
> [!IMPORTANT]
> Před stažením projektu určete důvěryhodnost kódu.  
  
## <a name="project-file"></a><a name="BKMK_ProjectFile"></a> Soubor projektu  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] používá formát souboru projektu založeného na jazyce XML, který je jednoduchý a rozšiřitelný. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Formát souboru projektu umožňuje vývojářům popsat položky, které mají být sestaveny, a také způsob jejich sestavení pro různé operační systémy a konfigurace. Kromě toho formát souboru projektu umožňuje vývojářům vytvářet opakovaně použitelná pravidla sestavení, která lze připravit na samostatné soubory, aby sestavení lze provádět konzistentně napříč různými projekty v produktu.  
  
 V následujících částech jsou popsány některé základní prvky [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] formátu souboru projektu. Kurz o tom, jak vytvořit základní soubor projektu, naleznete v tématu [Návod: vytvoření souboru projektu MSBuild od začátku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).  
  
### <a name="properties"></a><a name="BKMK_Properties"></a> Vlastnosti  
 Vlastnosti reprezentující páry klíč/hodnota, které lze použít ke konfiguraci sestavení. Vlastnosti jsou deklarovány vytvořením prvku, který má název vlastnosti jako podřízený prvek elementu [Property](../msbuild/propertygroup-element-msbuild.md) . Například následující kód vytvoří vlastnost s názvem `BuildDir` , která má hodnotu `Build` .  
  
```  
<PropertyGroup>  
    <BuildDir>Build</BuildDir>  
</PropertyGroup>  
```  
  
 Můžete definovat vlastnost podmíněně umístěním `Condition` atributu v elementu. Obsah podmíněných elementů je ignorován, pokud není podmínka vyhodnocena jako `true` . V následujícím příkladu `Configuration` je definován prvek, pokud ještě nebyl definován.  
  
```  
<Configuration  Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
```  
  
 Na vlastnosti lze odkazovat v rámci souboru projektu pomocí syntaxe $ (*PropertyName*). Například můžete odkazovat na vlastnosti v předchozích příkladech pomocí `$(BuildDir)` a `$(Configuration)` .  
  
 Další informace o vlastnostech naleznete v tématu [MSBuild Properties](msbuild-properties1.md).  
  
### <a name="items"></a><a name="BKMK_Items"></a> Položek  
 Položky jsou vstupy do systému sestavení a obvykle reprezentují soubory. Položky jsou seskupeny do typů položek na základě uživatelsky definovaných názvů položek. Tyto typy položek lze použít jako parametry pro úlohy, které používají jednotlivé položky k provedení kroků procesu sestavení.  
  
 Položky jsou deklarovány v souboru projektu vytvořením prvku, který má název typu položky jako podřízený prvek skupiny [Item](../msbuild/itemgroup-element-msbuild.md) . Například následující kód vytvoří typ položky s názvem `Compile` , který obsahuje dva soubory.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 Na typy položek lze odkazovat v rámci souboru projektu pomocí syntaxe @ (*ItemType*). Například typ položky v příkladu se odkazuje pomocí `@(Compile)` .  
  
 V nástroji MSBuild názvy elementů a atributů rozlišují velká a malá písmena. Názvy vlastností, položek a metadat však nejsou. Následující příklad vytvoří typ položky `Compile` , `comPile` nebo jakoukoli jinou variaci velikosti písmen a poskytne položce Typ hodnota One. cs; Two. cs.  
  
```  
<ItemGroup>  
  <Compile Include="one.cs" />  
  <comPile Include="two.cs" />  
</ItemGroup>  
```  
  
 Položky mohou být deklarovány pomocí zástupných znaků a mohou obsahovat další metadata pro pokročilejší scénáře sestavení. Další informace o položkách naleznete v tématu [Items](../msbuild/msbuild-items.md).  
  
### <a name="tasks"></a><a name="BKMK_Tasks"></a> Provádění  
 Úlohy jsou jednotky spustitelného kódu, který [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projekty používají k provádění operací sestavení. Například úloha může kompilovat vstupní soubory nebo spustit externí nástroj. Úlohy se dají znovu použít a můžou je sdílet s různými vývojáři v různých projektech.  
  
 Logika spuštění úkolu je zapsána ve spravovaném kódu a mapována na pomocí [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] elementu [UsingTask](../msbuild/usingtask-element-msbuild.md) . Vlastní úlohu můžete napsat vytvářením spravovaného typu, který implementuje <xref:Microsoft.Build.Framework.ITask> rozhraní. Další informace o tom, jak psát úlohy, najdete v tématu [psaní úloh](../msbuild/task-writing.md).  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zahrnuje běžné úlohy, které můžete upravit tak, aby vyhovovaly vašim požadavkům.  Příklady jsou [kopie](../msbuild/copy-task.md), které kopírují soubory, [MakeDir –](../msbuild/makedir-task.md), které vytvářejí adresáře a [CSC](../msbuild/csc-task.md), které kompiluje soubory zdrojového kódu jazyka Visual C#. Seznam dostupných úloh spolu s informacemi o použití naleznete v tématu [Task reference](../msbuild/msbuild-task-reference.md).  
  
 Úloha je spuštěna v [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] souboru projektu vytvořením prvku, který má název úkolu jako podřízený prvek [cílového](../msbuild/target-element-msbuild.md) prvku. Úlohy obvykle přijímají parametry, které jsou předány jako atributy elementu. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Jako parametry lze použít jak vlastnosti, tak položky. Například následující kód volá úlohu [MakeDir –](../msbuild/makedir-task.md) a předá jí hodnotu `BuildDir` vlastnosti, která byla deklarována v předchozím příkladu.  
  
```  
<Target Name="MakeBuildDirectory">  
    <MakeDir  Directories="$(BuildDir)" />  
</Target>  
```  
  
 Další informace o úlohách najdete v tématu [úlohy](../msbuild/msbuild-tasks.md).  
  
### <a name="targets"></a><a name="BKMK_Targets"></a> Cíle  
 Cílí seskupení úkolů v určitém pořadí a vystavení oddílů souboru projektu jako vstupní body do procesu sestavení. Cíle jsou často seskupené do logických oddílů ke zvýšení čitelnosti a k umožnění rozšíření. Přerušení kroků sestavení do cílů umožňuje volat jednu část procesu sestavení z jiných cílů bez kopírování tohoto oddílu kódu do každého cíle. Například pokud několik vstupních bodů do procesu sestavení vyžaduje, aby byly sestaveny odkazy, můžete vytvořit cíl, který sestaví odkazy a potom spustí tento cíl z každého vstupního bodu, kde je vyžadován.  
  
 Cíle jsou deklarovány v souboru projektu pomocí [cílového](../msbuild/target-element-msbuild.md) prvku. Například následující kód vytvoří cíl s názvem `Compile` , který pak zavolá úlohu [CSC](../msbuild/csc-task.md) , která má seznam položek deklarovaný v předchozím příkladu.  
  
```  
<Target Name="Compile">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 V pokročilejších scénářích lze cíle použít k popisu vztahů mezi sebou a provádět analýzu závislostí, aby bylo možné přeskočit celé části procesu sestavení, pokud je tento cíl aktuální. Další informace o cílech najdete v tématu [cíle](../msbuild/msbuild-targets.md).  
  
## <a name="build-logs"></a><a name="BKMK_BuildLogs"></a> Protokoly sestavení  
 Zprávy o chybách, upozorněních a zprávách sestavení můžete protokolovat do konzoly nebo jiného výstupního zařízení. Další informace najdete v tématu [získání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md) a [protokolování v nástroji MSBuild](../msbuild/logging-in-msbuild.md).  
  
## <a name="using-msbuild-in-visual-studio"></a><a name="BKMK_VisualStudio"></a> Použití nástroje MSBuild v aplikaci Visual Studio  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] používá [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Formát souboru projektu k ukládání informací o sestavení o spravovaných projektech. Nastavení projektu, která jsou přidána nebo změněna pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozhraní, se projeví v souboru. * proj, který je generován pro každý projekt. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] používá hostovanou instanci [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pro sestavení spravovaných projektů. To znamená, že spravovaný projekt může být sestaven v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nebo na příkazovém řádku (i když [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] není nainstalován) a výsledky budou identické.  
  
 Kurz týkající se použití nástroje MSBuild v aplikaci Visual Studio naleznete v tématu [Návod: použití nástroje MSBuild](../msbuild/walkthrough-using-msbuild.md).  
  
## <a name="multitargeting"></a><a name="BKMK_Multitargeting"></a> Cílení na více verzí  
 Pomocí sady Visual Studio můžete zkompilovat aplikaci pro spuštění v některé z několika verzí .NET Framework. Například můžete zkompilovat aplikaci pro spuštění na .NET Framework 2,0 na 32 platformě a můžete zkompilovat stejnou aplikaci, aby běžela na .NET Framework 4,5 64 na 16bitové platformě. Možnost kompilace do více než jednoho rozhraní se nazývá cílení na více verzí.  
  
 Toto jsou některé z výhod cílení na více verzí:  
  
- Můžete vyvíjet aplikace, které cílí na starší verze .NET Framework, například verze 2,0, 3,0 a 3,5.  
  
- Můžete cílit na jiné architektury než .NET Framework, například na Silverlight.  
  
- Můžete cílit na *profil rozhraní*, což je předdefinovaná podmnožina cílové architektury.  
  
- Pokud se uvolní aktualizace Service Pack pro aktuální verzi .NET Framework, můžete na ni cílit.  
  
- Cílení na více verzí zaručuje, že aplikace používá pouze funkce, které jsou k dispozici v cílové architektuře a platformě.  
  
  Další informace najdete v tématu [cílení](../msbuild/msbuild-multitargeting-overview.md)na více verzí.  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Návod: vytvoření souboru projektu MSBuild od začátku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)|Ukazuje, jak vytvořit soubor základního projektu přírůstkově pomocí pouze textového editoru.|  
|[Návod: Použití nástroje MSBuild](../msbuild/walkthrough-using-msbuild.md)|Zavádí stavební kameny nástroje MSBuild a ukazuje, jak psát, manipulovat a ladit projekty MSBuild bez zavření prostředí IDE sady Visual Studio.|  
|[Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)|Představuje čtyři stavební kameny nástroje MSBuild: vlastnosti, položky, cíle a úkoly.|  
|[Položky](../msbuild/msbuild-items.md)|V této části najdete popis obecných konceptů za [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] formátem souboru a způsobu, jakým se tyto části vejdou dohromady.|  
|[Vlastnosti nástroje MSBuild](msbuild-properties1.md)|Zavádí vlastnosti a kolekce vlastností. Vlastnosti jsou páry klíč/hodnota, které lze použít ke konfiguraci sestavení.|  
|[Targets](../msbuild/msbuild-targets.md)|Vysvětluje, jak seskupit úkoly společně v určitém pořadí a povolit části procesu sestavení, které mají být volány v příkazovém řádku.|  
|[Úlohy](../msbuild/msbuild-tasks.md)|Ukazuje, jak vytvořit jednotku spustitelného kódu, který lze použít [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] k provedení atomických operací sestavení.|  
|[Podmínky](../msbuild/msbuild-conditions.md)|Popisuje, jak používat `Condition` atribut v elementu MSBuild.|  
|[Pokročilé koncepty](../msbuild/msbuild-advanced-concepts.md)|Prezentuje dávkování, provádění transformací, cílení na více verzí a další pokročilé techniky.|  
|[Protokolování v nástroji MSBuild](../msbuild/logging-in-msbuild.md)|Popisuje, jak protokolovat události sestavení, zprávy a chyby.|  
|[Další zdroje informací](../msbuild/additional-msbuild-resources.md)|Obsahuje seznam prostředků komunity a podpory, kde najdete další informace o nástroji MSBuild.|  
  
## <a name="reference"></a>Odkaz  
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)  
 Obsahuje odkazy na témata, která obsahují referenční informace.  
  
 Glosář  
 Definuje společné výrazy MSBuild.
