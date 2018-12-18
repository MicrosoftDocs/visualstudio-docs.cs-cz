---
title: Referenční dokumentace úlohy nástroje MSBuild | Dokumentace Microsoftu
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
- MSBuild, tasks
ms.assetid: b3144b27-a426-4259-b8ae-5f7991b202b6
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6f1767ce1c572e1e3d8eacae8ba3a60f3593476
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193985"
---
# <a name="msbuild-task-reference"></a>Referenční dokumentace úlohy nástroje MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Úlohy poskytují kód, který se spustí během procesu sestavení. Úkoly v následujícím seznamu jsou součástí [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Když [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] je nainstalovaný, další úkoly jsou k dispozici, které se používají k vytváření [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projekty. Další informace najdete v tématu [Visual C++ – úkoly](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).  
  
 Kromě uvedených v tématech v této části parametrů také každý úkol má následující parametry:  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Condition`|Volitelné `String` parametru.<br /><br /> A `Boolean` výraz, který [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] modul se používá k určení, zda se tato úloha spustí. Informace o podmínkách, které jsou podporovány [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], naleznete v tématu [podmínky](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Volitelný parametr. Může obsahovat jednu z následujících hodnot:<br /><br /> -   **WarnAndContinue** nebo **true**. Při selhání úkolu, následné úlohy v [cílové](../msbuild/target-element-msbuild.md) elementu a sestavení budou dál spouštět a všechny chyby z úlohy jsou považovány za upozornění.<br />-   **ErrorAndContinue**. Při selhání úkolu, následné úlohy v `Target` elementu a sestavení budou dál spouštět a všechny chyby z úlohy jsou považována za chyby.<br />-   **ErrorAndStop** nebo **false** (výchozí). Při selhání úkolu, ve zbývajících úkolech v `Target` elementu a sestavení nejsou provedeny a celé `Target` elementu a sestavení se považuje za neúspěšný.<br /><br /> Verze rozhraní .NET Framework před 4.5 podporována pouze `true` a `false` hodnoty.<br /><br /> Další informace najdete v tématu [postupy: ignorování chyb v úlohách](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Base – základní třída](../msbuild/task-base-class.md)  
 Přidá několik parametrů do úlohy, které jsou odvozeny z <xref:Microsoft.Build.Utilities.Task> třídy.  
  
 [TaskExtension – základní třída](../msbuild/taskextension-base-class.md)  
 Přidá několik parametrů do úlohy, které jsou odvozeny z <xref:Microsoft.Build.Tasks.TaskExtension> třídy.  
  
 [ToolTaskExtension – základní třída](../msbuild/tooltaskextension-base-class.md)  
 Přidá několik parametrů do úlohy, které jsou odvozeny z <xref:Microsoft.Build.Tasks.ToolTaskExtension> třídy.  
  
 [AL (linker sestavení) – úloha](../msbuild/al-assembly-linker-task.md)  
 Vytvoří sestavení s manifestem z jednoho nebo více souborů, které jsou buď moduly nebo souborů prostředků.  
  
 [AspNetCompiler – úloha](../msbuild/aspnetcompiler-task.md)  
 Zabalí aspnet_compiler.exe, nástroj pro předkompilaci aplikace ASP.NET.  
  
 [AssignCulture – úloha](../msbuild/assignculture-task.md)  
 Přiřadí identifikátory jazykové verze položky.  
  
 [AssignProjectConfiguration – úloha](../msbuild/assignprojectconfiguration-task.md)  
 Přijímá seznam řetězců, konfigurace a přiřadí ho k zadaným projektům.  
  
 [AssignTargetPath – úloha](../msbuild/assigntargetpath-task.md)  
 Přijímá seznam souborů a přidá `<TargetPath>` atributy, pokud již nejsou určeny.  
  
 [CallTarget – úloha](../msbuild/calltarget-task.md)  
 Vyvolá cíl v souboru projektu.  
  
 [CombinePath – úloha](../msbuild/combinepath-task.md)  
 Zkombinuje zadané cesty do jedné cesty.  
  
 [ConvertToAbsolutePath – úloha](../msbuild/converttoabsolutepath-task.md)  
 Převede relativní cestu nebo odkazu na absolutní cestu.  
  
 [Copy – úloha](../msbuild/copy-task.md)  
 Zkopíruje soubory do nového umístění.  
  
 [CreateCSharpManifestResourceName – úloha](../msbuild/createcsharpmanifestresourcename-task.md)  
 Vytvoří [!INCLUDE[csprcs](../includes/csprcs-md.md)]– název manifestu stylu z názvu souboru .resx dané nebo jiný prostředek.  
  
 [CreateItem – úloha](../msbuild/createitem-task.md)  
 Naplní kolekcí položek ze vstupních položek, což položky, které se mají zkopírovat z jednoho seznamu do jiného.  
  
 [CreateProperty – úloha](../msbuild/createproperty-task.md)  
 Naplní vlastnosti ze vstupních hodnot, což hodnoty zkopírovány z jedné vlastnosti nebo řetězec do druhého.  
  
 [CreateVisualBasicManifestResourceName – úloha](../msbuild/createvisualbasicmanifestresourcename-task.md)  
 Vytvoří [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]– název manifestu stylu z názvu souboru .resx dané nebo jiný prostředek.  
  
 [Csc – úloha](../msbuild/csc-task.md)  
 Vyvolá kompilátor Visual C# k vytvoření spustitelné soubory, knihovny DLL nebo moduly kódu.  
  
 [Delete – úloha](../msbuild/delete-task.md)  
 Odstraní zadané soubory.  
  
 [Error – úloha](../msbuild/error-task.md)  
 Sestavení se zastaví a protokoly chybu na základě Vyhodnocená podmíněného příkazu.  
  
 [Exec – úloha](../msbuild/exec-task.md)  
 Spustí zadaný program nebo příkaz pomocí zadaných argumentů.  
  
 [FindAppConfigFile – úloha](../msbuild/findappconfigfile-task.md)  
 Vyhledá soubor app.config, pokud některý z zadaný seznamů.  
  
 [FindInList – úloha](../msbuild/findinlist-task.md)  
 Vyhledá položky v zadaném seznamu, který má odpovídající itemspec.  
  
 [FindUnderPath – úloha](../msbuild/findunderpath-task.md)  
 Určuje položky, které v kolekci zadaná položka existuje v zadané složce a všechny její podsložky.  
  
 [FormatUrl – úloha](../msbuild/formaturl-task.md)  
 Převede adresu URL na správném formátu adresy URL.  
  
 [FormatVersion – úloha](../msbuild/formatversion-task.md)  
 Číslo revize připojí číslo verze.  
  
 [GenerateApplicationManifest – úloha](../msbuild/generateapplicationmanifest-task.md)  
 Generuje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest aplikace nebo nativní manifest.  
  
 [GenerateBootstrapper – úloha](../msbuild/generatebootstrapper-task.md)  
 Poskytuje automatizovaný způsob, jak zjistit, stáhnout a nainstalovat aplikace a její požadované součásti.  
  
 [GenerateDeploymentManifest – úloha](../msbuild/generatedeploymentmanifest-task.md)  
 Generuje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu nasazení.  
  
 [GenerateResource – úloha](../msbuild/generateresource-task.md)  
 Převádí soubory .txt a .resx na common language runtime binárních souborů .resources.  
  
 [GenerateTrustInfo – úloha](../msbuild/generatetrustinfo-task.md)  
 Generuje důvěryhodnost aplikace z manifestu základní a `TargetZone` a `ExcludedPermissions` parametry.  
  
 [GetAssemblyIdentity – úloha](../msbuild/getassemblyidentity-task.md)  
 Načte identit sestavení ze zadaných souborů a vypíše informace o identitě.  
  
 [GetFrameworkPath – úloha](../msbuild/getframeworkpath-task.md)  
 Načte cestu k [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sestavení.  
  
 [GetFrameworkSdkPath – úloha](../msbuild/getframeworksdkpath-task.md)  
 Načte cestu k [!INCLUDE[winsdklong](../includes/winsdklong-md.md)].  
  
 [GetReferenceAssemblyPaths – úloha](../msbuild/getreferenceassemblypaths-task.md)  
 Vrátí odkaz na sestavení cesty různých platforem.  
  
 [LC – úloha](../msbuild/lc-task.md)  
 Generuje soubor .license z soubor .licx.  
  
 [MakeDir – úloha](../msbuild/makedir-task.md)  
 Vytvoří adresářů a v případě potřeby všechny nadřazené adresáře.  
  
 [Message – úloha](../msbuild/message-task.md)  
 Zaznamená zprávu během sestavení.  
  
 [Move – úloha](../msbuild/move-task.md)  
 Soubory přesunou do nového umístění.  
  
 [MSBuild – úloha](../msbuild/msbuild-task.md)  
 Sestaví [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projekty z jiného [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektu.  
  
 [ReadLinesFromFile – úloha](../msbuild/readlinesfromfile-task.md)  
 Načte seznam položek z textového souboru.  
  
 [RegisterAssembly – úloha](../msbuild/registerassembly-task.md)  
 Načte metadata v rámci zadaného sestavení a přidá nezbytné položky registru.  
  
 [RemoveDir – úloha](../msbuild/removedir-task.md)  
 Odebere zadaný adresáře a všechny jeho soubory a podadresáře.  
  
 [RemoveDuplicates – úloha](../msbuild/removeduplicates-task.md)  
 Odebere duplicitní položky z kolekce zadané položky.  
  
 [RequiresFramework35SP1Assembly – úloha](../msbuild/requiresframework35sp1assembly-task.md)  
 Určuje, zda aplikace požaduje instalaci rozhraní .NET Framework 3.5 SP1.  
  
 Úloha ResGen  
 Zastaralé. Použití [generateresource – úloha](../msbuild/generateresource-task.md) úloh k převedení souborů TXT a resx do a z common language runtime binárních souborů .resources.  
  
 [ResolveAssemblyReference – úloha](../msbuild/resolveassemblyreference-task.md)  
 Určuje všechna sestavení, které jsou závislé na zadaná sestavení.  
  
 [ResolveComReference – úloha](../msbuild/resolvecomreference-task.md)  
 Přebírá seznam názvů knihoven typů nebo souborů .tlb a řeší tyto knihovny typů do umístění na disku.  
  
 [ResolveKeySource – úloha](../msbuild/resolvekeysource-task.md)  
 Určuje zdroj klíče silného názvu  
  
 [ResolveManifestFiles – úloha](../msbuild/resolvemanifestfiles-task.md)  
 Řeší následující položky v procesu sestavení k souborům pro generování manifestu: vytvořené položky, závislosti, satelity, obsah, symboly ladění a dokumentaci.  
  
 [ResolveNativeReference – úloha](../msbuild/resolvenativereference-task.md)  
 Nativní odkazy řeší.  
  
 [ResolveNonMSBuildProjectOutput – úloha](../msbuild/resolvenonmsbuildprojectoutput-task.md)  
 Určuje výstupní soubory pro odkazy na projekt bez MSBuild.  
  
 [SGen – úloha](../msbuild/sgen-task.md)  
 Vytvoří sestavení serializace XML pro typy v zadaném sestavení.  
  
 [SignFile – úloha](../msbuild/signfile-task.md)  
 Zaregistruje zadaného souboru pomocí zadaného certifikátu.  
  
 [Touch – úloha](../msbuild/touch-task.md)  
 Nastaví dobu přístup a úpravy souborů.  
  
 [UnregisterAssembly – úloha](../msbuild/unregisterassembly-task.md)  
 Zruší registraci zadaného sestavení pro účely vzájemné spolupráce COM.  
  
 [UpdateManifest – úloha](../msbuild/updatemanifest-task.md)  
 Aktualizace vybraných vlastností v manifestu a vzdává.  
  
 [Vbc – úloha](../msbuild/vbc-task.md)  
 Vyvolá kompilátor jazyka Visual Basic vytvoří spustitelné soubory, knihovny DLL nebo moduly kódu...  
  
 [Warning – úloha](../msbuild/warning-task.md)  
 Protokoly upozornění během sestavení podle Vyhodnocená podmíněném příkazu.  
  
 [WriteCodeFragment – úloha](../msbuild/writecodefragment-task.md)  
 Generuje soubor kódu dočasný pomocí fragmentu generovaného kódu. Nedojde k odstranění souboru.  
  
 [WriteLinesToFile – úloha](../msbuild/writelinestofile-task.md)  
 Zapíše zadaných položek do zadaného textového souboru.  
  
 [XmlPeek – úloha](../msbuild/xmlpeek-task.md)  
 Vrací hodnoty podle specifikace dotazu XPath ze souboru XML.  
  
 [XmlPoke – úloha](../msbuild/xmlpoke-task.md)  
 Nastaví hodnoty podle specifikace dotazu XPath do souboru XML.  
  
 [XslTransformation – úloha](../msbuild/xsltransformation-task.md)  
 Transformuje vstupní XML pomocí *Extensible transformaci šablony stylů jazyk* (XSLT) nebo kompilované XSLT a výstupů na zařízení s výstupní soubor nebo soubor.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)   
 [Zápis úloh](../msbuild/task-writing.md)   
 [Úlohy](../msbuild/msbuild-tasks.md)



