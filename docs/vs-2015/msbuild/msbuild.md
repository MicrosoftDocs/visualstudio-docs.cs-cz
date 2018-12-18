---
title: Nástroj MSBuild | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, about MSBuild
- MSBuild, overview
ms.assetid: e39f13f7-1e1d-4435-95ca-0c222bca071c
caps.latest.revision: 62
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a2ca3a14c1e4e35da4e8cddfdecb0346740286a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837760"
---
# <a name="msbuild"></a>MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] Je platforma pro vytváření aplikací. Tento modul, který se také nazývá MSBuild, obsahuje schéma XML souboru projektu, který určuje, jak platforma sestavení zpracuje a vytvoří software. Visual Studio používá MSBuild, ale není závislé na Visual Studio. Vyvoláním msbuild.exe v souboru projektu nebo řešení můžete organizovat a vytvářet produkty v prostředích, kde není nainstalovaná sada Visual Studio.  
  
 Visual Studio používá MSBuild k načtení a sestavení spravovaných projektů. Soubory projektu v sadě Visual Studio (CSPROJ, vbproj, vcxproj a jiné) obsahují kód XML nástroje MSBuild, který se spustí po sestavení projektu s použitím rozhraní IDE. Importovat všechna potřebná nastavení projektů sady Visual Studio a vytvoří procesy pro typickou vývojovou práci, ale můžete je rozšířit nebo upravit z aplikace Visual Studio nebo pomocí editoru XML.  
  
 Informace o nástroji MSBuild jazyka C++, naleznete v tématu [MSBuild (Visual C++)](http://msdn.microsoft.com/library/7a1be7ff-0312-4669-adf2-5f5bf507d560).  
  
 Následující příklady ilustrují, kdy můžete spustit sestavení pomocí příkazového řádku MSBuild namísto rozhraní IDE sady Visual Studio.  
  
- Visual Studio není nainstalována.  
  
- Chcete použít 64bitovou verzi nástroje MSBuild. Tato verze nástroje MSBuild je obvykle nepotřebná, ale umožňuje MSBuild přístup k více paměti.  
  
- Chcete spustit sestavení ve více procesech. Můžete však použít rozhraní IDE k dosažení stejného výsledku v projektech v jazyce C++ a C#.  
  
- Chcete změnit systém sestavení. Například můžete chtít povolit následující akce:  
  
  -   Předběžné zpracujte soubory, než dosáhnou kompilátoru.  
  
  -   Zkopírujte výstupy sestavení na jiné místo.  
  
  -   Vytvořte komprimované soubory z výstupů sestavení.  
  
  -   Proveďte krok následného zpracování. Můžete například chtít razítko sestavení s jinou verzí.  
  
  V integrovaném vývojovém prostředí sady Visual Studio můžete napsat kód, ale spustit sestavení pomocí nástroje MSBuild. Jako další alternativu můžete sestavit kód v rozhraní IDE na vývojovém počítači, ale pomocí příkazového řádku MSBuild sestavit kód, který je integrován od více vývojářů.  
  
> [!NOTE]
>  Team Foundation Build můžete použít k automatické kompilaci, testování, nasazení aplikace. Systém sestavení může automaticky spouštět sestavení, pokud vývojáři vrácení kódu se změnami (například jako součást strategie Nepřetržitá integrace) nebo podle plánu (například noční sestavení ověřovacího testu sestavení). Team Foundation Build kompiluje kód pomocí nástroje MSBuild. Další informace najdete v tématu [sestavte aplikaci](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692).  
  
 Toto téma obsahuje přehled MSBuild. Úvodní tutoriál naleznete v tématu [návod: použití nástroje MSBuild](../msbuild/walkthrough-using-msbuild.md).  
  
 **V tomto tématu**  
  
-   [Použití nástroje MSBuild na příkazovém řádku](#BKMK_CommandPrompt)  
  
-   [Soubor projektu](#BKMK_ProjectFile)  
  
    -   [Vlastnosti](#BKMK_Properties)  
  
    -   [Položky](#BKMK_Items)  
  
    -   [Úlohy](#BKMK_Tasks)  
  
    -   [Cíle](#BKMK_Targets)  
  
-   [Protokoly o sestavení](#BKMK_BuildLogs)  
  
-   [Použití nástroje MSBuild v sadě Visual Studio](#BKMK_VisualStudio)  
  
-   [Cílení na více verzí](#BKMK_Multitargeting)  
  
##  <a name="BKMK_CommandPrompt"></a> Použití nástroje MSBuild na příkazovém řádku  
 Ke spuštění [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] příkazového řádku, předejte soubor projektu MSBuild.exe spolu s příslušnými parametry příkazového řádku. Možnosti příkazového řádku umožňují nastavit vlastnosti, zvláštní cíle a nastavit další možnosti, které řízení procesu sestavení. Třeba, použijte následující syntaxi příkazového řádku pro sestavení souboru `MyProj.proj` s `Configuration` nastavenou na `Debug`.  
  
```  
MSBuild.exe MyProj.proj /property:Configuration=Debug  
```  
  
 Další informace o [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] možnosti příkazového řádku najdete v tématu [Reference k příkazovému řádku](../msbuild/msbuild-command-line-reference.md).  
  
> [!IMPORTANT]
>  Před stažením projektu určete důvěryhodnost kódu.  
  
##  <a name="BKMK_ProjectFile"></a> Soubor projektu  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] používá formát souboru projektu založeného na XML, který je jednoduchý a rozšiřitelný. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Formát souboru projektu umožňuje vývojářům popsat položky, které mají být vytvořeny, a také jak mají být sestaveny pro různé operační systémy a konfigurace. Kromě toho formát souboru projektu umožňuje vývojářům vytvářet opakovaná pravidla sestavení, které můžete promítnout do samostatných souborů tak, aby sestavení mohou být provedena konzistentně v různých projektech v rámci produktu.  
  
 Následující části popisují některé základní elementy [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] formát souboru projektu. Kurz o tom, jak vytvořit soubor základního projektu, najdete v tématu [návod: vytvoření souboru projektu MSBuild od začátku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).  
  
###  <a name="BKMK_Properties"></a> Vlastnosti  
 Vlastnosti představují páry klíč/hodnota, které můžete použít ke konfiguraci sestavení. Vlastnosti jsou deklarovány vytvořením prvku, který má název vlastnosti jako podřízený objekt [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) elementu. Například následující kód vytvoří vlastnost s názvem `BuildDir` , který má hodnotu `Build`.  
  
```  
<PropertyGroup>  
    <BuildDir>Build</BuildDir>  
</PropertyGroup>  
```  
  
 Můžete definovat vlastnost podmíněně umístěním `Condition` atribut v elementu. Obsah podmíněných prvků se ignoruje, pokud je podmínka vyhodnocena jako `true`. V následujícím příkladu `Configuration` prvku je definováno, pokud ještě nebyly definovány.  
  
```  
<Configuration  Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
```  
  
 Vlastnosti lze odkazovat v rámci souboru projektu pomocí syntaxe $(*PropertyName*). Například vlastnosti v předchozích příkladech můžete odkazovat pomocí `$(BuildDir)` a `$(Configuration)`.  
  
 Další informace o vlastnostech najdete v tématu [vlastnosti nástroje MSBuild](msbuild-properties1.md).  
  
###  <a name="BKMK_Items"></a> Položky  
 Položky jsou vstupy do systému sestavení a obvykle představují soubory. Položky jsou seskupeny do typů položek podle uživatelem definovanou položku katalogu názvy. Tyto typy položek lze použít jako parametry pro úkoly, které používají jednotlivé položky k provedení kroků procesu sestavení.  
  
 Položky jsou deklarovány v souboru projektu vytvořením prvku, který má název typu položky jako podřízený objekt [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elementu. Například následující kód vytvoří typ položky s názvem `Compile`, který obsahuje dva soubory.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 Typy položek lze odkazovat v rámci souboru projektu pomocí syntaxe @(*ItemType*). Například typ položky v tomto příkladu by odkazovat pomocí `@(Compile)`.  
  
 V nástroji MSBuild názvy prvků a atributů jsou malá a velká písmena. Nicméně názvy vlastnosti, položky a metadat nejsou. Následující příklad vytvoří typ položky `Compile`, `comPile`, nebo jinou variaci a dá typu položky hodnotu "one.cs;two.cs".  
  
```  
<ItemGroup>  
  <Compile Include="one.cs" />  
  <comPile Include="two.cs" />  
</ItemGroup>  
```  
  
 Položky mohou být deklarovány pomocí zástupných znaků a může obsahovat další metadata pro více pokročilejších scénářů sestavení. Další informace o položkách naleznete v tématu [položky](../msbuild/msbuild-items.md).  
  
###  <a name="BKMK_Tasks"></a> Úlohy  
 Úkoly jsou jednotky spustitelného kódu, který [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projekty používají k provádění operací sestavení. Úkol může například kompilovat vstupní soubory nebo spustit externí nástroj. Úlohy lze znovu použít, a sdíleny s různými vývojáři v různých projektech.  
  
 Logika spuštění úkolu je zapsána ve spravovaném kódu a namapována na [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pomocí [UsingTask](../msbuild/usingtask-element-msbuild.md) elementu. Můžete napsat vlastní úkol vytvořením spravovaného typu, který implementuje <xref:Microsoft.Build.Framework.ITask> rozhraní. Další informace o tom, jak psát úkoly, naleznete v tématu [zápis úloh](../msbuild/task-writing.md).  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] obsahuje běžné úkoly, které lze upravit tak, aby vyhovoval vašim požadavkům.  Mezi příklady patří [kopírování](../msbuild/copy-task.md), zkopírování souborů [MakeDir](../msbuild/makedir-task.md), vytvoření adresářů a [Csc](../msbuild/csc-task.md), který zkompiluje soubory zdrojového kódu Visual C#. Seznam dostupných úkolů a informace o jejich použití naleznete v tématu [– referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md).  
  
 Úloha je proveden v [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] souboru projektu vytvořením prvku, který má název úkolu jako podřízený objekt [cílové](../msbuild/target-element-msbuild.md) elementu. Úkoly obvykle přijímají parametry, které jsou předány jako atributy elementu. Obě [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] vlastností a položek lze použít jako parametry. Například následující kód volá [MakeDir](../msbuild/makedir-task.md) úloh a předává jeho hodnotu `BuildDir` , která byla definována v předchozím příkladu.  
  
```  
<Target Name="MakeBuildDirectory">  
    <MakeDir  Directories="$(BuildDir)" />  
</Target>  
```  
  
 Další informace o úlohách najdete v tématu [úlohy](../msbuild/msbuild-tasks.md).  
  
###  <a name="BKMK_Targets"></a> Cíle  
 Cíle seskupují úkoly v určitém pořadí a vystavují oddíly souborů projektu jako vstupní body do procesu sestavení. Cíle jsou často seskupeny do logických částí pro zvýšení přehlednosti a pro možnosti rozšíření. Přepnutí kroků sestavení do cílů vám umožňuje volat jednu část procesu sestavení z jiných cílů bez kopírování příslušné části kódu do každého cíle. Například pokud několik vstupních bodů do procesu sestavení vyžaduje sestavení odkazů, můžete vytvořit cíl, který vytváří odkazy a poté spustit tento cíl z každého vstupního bodu, kde je to požadováno.  
  
 Cíle jsou deklarovány v souboru projektu pomocí [cílové](../msbuild/target-element-msbuild.md) elementu. Například následující kód vytvoří cíl s názvem `Compile`, který pak volá [Csc](../msbuild/csc-task.md) úlohu, která obsahuje seznam položek, který byl deklarován v předchozím příkladu.  
  
```  
<Target Name="Compile">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 V pokročilejších scénářích lze cíle použít k popisu vztahů mezi sebou a provést analýzu závislostí tak, aby celé části procesu sestavení mohly být přeskočeny, pokud tento cíl je aktuální. Další informace o cílech naleznete v tématu [cíle](../msbuild/msbuild-targets.md).  
  
##  <a name="BKMK_BuildLogs"></a> Protokoly o sestavení  
 Můžete protokolovat chyby sestavení, varování a zprávy na konzole nebo jiném výstupním zařízení. Další informace najdete v tématu [získávání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md) a [protokolování v nástroji MSBuild](../msbuild/logging-in-msbuild.md).  
  
##  <a name="BKMK_VisualStudio"></a> Použití nástroje MSBuild v sadě Visual Studio  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] používá [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] formát souboru projektu k ukládání informací o sestavení o spravovaných projektech. Nastavení projektu, které je přidáno nebo změněno pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozhraní se projeví v. * proj soubor, který je generován pro každý projekt. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] používá hostované instance [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pro sestavení spravovaných projektů. To znamená, že spravovaný projekt může být součástí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nebo z příkazového řádku (i v případě [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] není nainstalována), a výsledky budou stejné.  
  
 Kurz o tom, jak používat MSBuild v sadě Visual Studio, najdete v tématu [návod: použití nástroje MSBuild](../msbuild/walkthrough-using-msbuild.md).  
  
##  <a name="BKMK_Multitargeting"></a> Cílení na více verzí  
 Pomocí sady Visual Studio můžete zkompilovat aplikaci pro spuštění v jedné z několika verzí rozhraní .NET Framework. Například můžete zkompilovat aplikaci pro spuštění v rozhraní .NET Framework 2.0 na 32bitové platformě a můžete zkompilovat stejnou aplikaci pro spuštění v rozhraní .NET Framework 4.5 na 64bitové platformě. Schopnosti kompilace pro více než jedno rozhraní jmenuje cílení na více verzí.  
  
 Toto jsou některé z výhod cílení na více verzí:  
  
- Můžete vyvíjet aplikace, které jsou cíleny na starší verze rozhraní .NET Framework, například verze 2.0, 3.0 a 3.5.  
  
- Můžete cílit rozhraní než .NET Framework, například Silverlight.  
  
- Můžete cílit *profil rozhraní*, což je předdefinovaná podmnožina cílového rozhraní framework.  
  
- Pokud bude vydána aktualizace service pack pro aktuální verzi rozhraní .NET Framework, může ji zaměřit.  
  
- Cílení na více verzí zaručuje, že aplikace používá pouze funkce, které jsou k dispozici v cílové architektury a platformy.  
  
  Další informace najdete v tématu [cílení na více verzí](../msbuild/msbuild-multitargeting-overview.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Návod: Vytvoření souboru projektu MSBuild od začátku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)|Ukazuje, jak vytvořit soubor základního projektu postupně pouze text pomocí editoru.|  
|[Návod: Použití nástroje MSBuild](../msbuild/walkthrough-using-msbuild.md)|Představuje stavebními bloky nástroje MSBuild a ukazuje, jak psát, manipulaci a ladit projekty MSBuild bez zavření Visual Studio IDE.|  
|[Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)|Nabízí čtyři stavební kameny nástroje MSBuild: vlastnosti, položky, cíle a úkoly.|  
|[Položky](../msbuild/msbuild-items.md)|Popisuje obecné principy za [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] souboru formátu a jak přizpůsobit kusy dohromady.|  
|[Vlastnosti nástroje MSBuild](msbuild-properties1.md)|Představuje vlastnosti a kolekce vlastností. Vlastnosti jsou páry klíč/hodnota, které lze použít ke konfiguraci sestavení.|  
|[Cíle](../msbuild/msbuild-targets.md)|Vysvětluje, jak seskupit úkoly společně v určitém pořadí a povolit oddíly procesu sestavení, která se má volat na příkazovém řádku.|  
|[Úlohy](../msbuild/msbuild-tasks.md)|Ukazuje, jak vytvořit jednotku spustitelného kódu, které mohou být využívána [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] k operacím atomického sestavení.|  
|[Podmínky](../msbuild/msbuild-conditions.md)|Tento článek popisuje způsob použití `Condition` atributy v prvku MSBuild.|  
|[Rozšířené koncepty](../msbuild/msbuild-advanced-concepts.md)|Představuje dávkování, provedení transformace, cílení na více verzí a dalších pokročilé techniky.|  
|[Protokolování v nástroji MSBuild](../msbuild/logging-in-msbuild.md)|Popisuje, jak protokolovat události sestavení, zprávy a chyby.|  
|[Další prostředky](../msbuild/additional-msbuild-resources.md)|Uvádí komunitu a prostředky podpory pro další informace o nástroji MSBuild.|  
  
## <a name="reference"></a>Odkaz  
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)  
 Obsahuje odkazy na témata, která obsahují referenční informace.  
  
 Slovníček  
 Definuje společné termíny MSBuild.





