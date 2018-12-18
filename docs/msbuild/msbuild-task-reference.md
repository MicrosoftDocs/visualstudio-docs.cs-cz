---
title: Referenční dokumentace úlohy nástroje MSBuild | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: b3144b27-a426-4259-b8ae-5f7991b202b6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 790d3e788fb04351fc379e8a4205e802c58516ad
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951142"
---
# <a name="msbuild-task-reference"></a>Referenční dokumentace úlohy nástroje MSBuild
Úlohy poskytují kód, který se spustí během procesu sestavení. Úkoly v následujícím seznamu jsou součástí [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Když [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] je nainstalovaný, další úkoly jsou k dispozici, které se používají k vytváření [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projekty. Další informace najdete v tématu [Visual C++ – úkoly](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).  

 Kromě uvedených v tématech v této části parametrů také každý úkol má následující parametry:  


| Parametr | Popis |
|-------------------| - |
| `Condition` | Volitelné `String` parametru.<br /><br /> A `Boolean` výraz, který [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] modul se používá k určení, zda se tato úloha spustí. Informace o podmínkách, které jsou podporovány [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], naleznete v tématu [podmínky](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Volitelný parametr. Může obsahovat jednu z následujících hodnot:<br /><br /> -   **WarnAndContinue** nebo **true**. Při selhání úkolu, následné úlohy v [cílové](../msbuild/target-element-msbuild.md) elementu a sestavení budou dál spouštět a všechny chyby z úlohy jsou považovány za upozornění.<br />-   **ErrorAndContinue**. Při selhání úkolu, následné úlohy v `Target` elementu a sestavení budou dál spouštět a všechny chyby z úlohy jsou považována za chyby.<br />-   **ErrorAndStop** nebo **false** (výchozí). Při selhání úkolu, ve zbývajících úkolech v `Target` elementu a sestavení nejsou provedeny a celé `Target` elementu a sestavení se považuje za neúspěšný.<br /><br /> Verze rozhraní .NET Framework před 4.5 podporována pouze `true` a `false` hodnoty.<br /><br /> Další informace najdete v tématu [postupy: ignorování chyb v úlohách](../msbuild/how-to-ignore-errors-in-tasks.md). |

## <a name="in-this-section"></a>V tomto oddílu  
 [Třída base úlohy](../msbuild/task-base-class.md)  
 Přidá několik parametrů do úlohy, které jsou odvozeny z <xref:Microsoft.Build.Utilities.Task> třídy.  

 [Taskextension – základní třída](../msbuild/taskextension-base-class.md)  
 Přidá několik parametrů do úlohy, které jsou odvozeny z <xref:Microsoft.Build.Tasks.TaskExtension> třídy.  

 [Tooltaskextension – základní třída](../msbuild/tooltaskextension-base-class.md)  
 Přidá několik parametrů do úlohy, které jsou odvozeny z <xref:Microsoft.Build.Tasks.ToolTaskExtension> třídy.  

 [AL (Linker sestavení) – úloha](../msbuild/al-assembly-linker-task.md)  
 Vytvoří sestavení s manifestem z jednoho nebo více souborů, které jsou buď moduly nebo souborů prostředků.  

 [AspNetCompiler – úloha](../msbuild/aspnetcompiler-task.md)  
 Zabalí *aspnet_compiler.exe*, nástroj pro předkompilaci aplikace ASP.NET.  

 [Assignculture – úloha](../msbuild/assignculture-task.md)  
 Přiřadí identifikátory jazykové verze položky.  

 [Assignprojectconfiguration – úloha](../msbuild/assignprojectconfiguration-task.md)  
 Přijímá seznam řetězců, konfigurace a přiřadí ho k zadaným projektům.  

 [Assigntargetpath – úloha](../msbuild/assigntargetpath-task.md)  
 Přijímá seznam souborů a přidá `<TargetPath>` atributy, pokud již nejsou určeny.  

 [Calltarget – úloha](../msbuild/calltarget-task.md)  
 Vyvolá cíl v souboru projektu.  

 [CombinePath – úloha](../msbuild/combinepath-task.md)  
 Zkombinuje zadané cesty do jedné cesty.  

 [Converttoabsolutepath – úloha](../msbuild/converttoabsolutepath-task.md)  
 Převede relativní cestu nebo odkazu na absolutní cestu.  

 [Copy – úloha](../msbuild/copy-task.md)  
 Zkopíruje soubory do nového umístění.  

 [Createcsharpmanifestresourcename – úloha](../msbuild/createcsharpmanifestresourcename-task.md)  
 Vytvoří [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-manifestu název stylu z danou *RESX* název souboru nebo jiného prostředku.  

 [Createitem – úloha](../msbuild/createitem-task.md)  
 Naplní kolekcí položek ze vstupních položek, což položky, které se mají zkopírovat z jednoho seznamu do jiného.  

 [CreateProperty – úloha](../msbuild/createproperty-task.md)  
 Naplní vlastnosti ze vstupních hodnot, což hodnoty zkopírovány z jedné vlastnosti nebo řetězec do druhého.  

 [Createvisualbasicmanifestresourcename – úloha](../msbuild/createvisualbasicmanifestresourcename-task.md)  
 Vytvoří [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]-manifestu název stylu z danou *RESX* název souboru nebo jiného prostředku.  

 [CSC – úloha](../msbuild/csc-task.md)  
 Vyvolá kompilátor Visual C# k vytvoření spustitelné soubory, knihovny DLL nebo moduly kódu.  

 [Delete – úloha](../msbuild/delete-task.md)  
 Odstraní zadané soubory.  

 [Úloha DownloadFile](../msbuild/downloadfile-task.md)  
 Stáhne soubor do zadaného umístění.  

 [Error – úloha](../msbuild/error-task.md)  
 Sestavení se zastaví a protokoly chybu na základě Vyhodnocená podmíněného příkazu.  

 [Exec – úloha](../msbuild/exec-task.md)  
 Spustí zadaný program nebo příkaz pomocí zadaných argumentů.  

 [Findappconfigfile – úloha](../msbuild/findappconfigfile-task.md)  
 Vyhledá *app.config* soubor, pokud existuje zadaný seznamů.  

 [Findinlist – úloha](../msbuild/findinlist-task.md)  
 Vyhledá položky v zadaném seznamu, který má odpovídající itemspec.  

 [Findunderpath – úloha](../msbuild/findunderpath-task.md)  
 Určuje položky, které v kolekci zadaná položka existuje v zadané složce a všechny její podsložky.  

 [Formaturl – úloha](../msbuild/formaturl-task.md)  
 Převede adresu URL na správném formátu adresy URL.  

 [Formatversion – úloha](../msbuild/formatversion-task.md)  
 Číslo revize připojí číslo verze.  

 [Generateapplicationmanifest – úloha](../msbuild/generateapplicationmanifest-task.md)  
 Generuje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikace nebo nativní manifest.  

 [GenerateBootstrapper – úloha](../msbuild/generatebootstrapper-task.md)  
 Poskytuje automatizovaný způsob, jak zjistit, stáhnout a nainstalovat aplikace a její požadované součásti.  

 [Generatedeploymentmanifest – úloha](../msbuild/generatedeploymentmanifest-task.md)  
 Generuje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestu nasazení.  

 [Generateresource – úloha](../msbuild/generateresource-task.md)  
 Převede *.txt* a *RESX* soubory do společného jazykového modulu runtime binární *.resources* soubory.  

 [Generatetrustinfo – úloha](../msbuild/generatetrustinfo-task.md)  
 Generuje důvěryhodnost aplikace z manifestu základní a `TargetZone` a `ExcludedPermissions` parametry.  

 [Getassemblyidentity – úloha](../msbuild/getassemblyidentity-task.md)  
 Načte identit sestavení ze zadaných souborů a vypíše informace o identitě.  

 [Getframeworkpath – úloha](../msbuild/getframeworkpath-task.md)  
 Načte cestu k [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] sestavení.  

 [Getframeworksdkpath – úloha](../msbuild/getframeworksdkpath-task.md)  
 Načte cestu k [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  

 [Getreferenceassemblypaths – úloha](../msbuild/getreferenceassemblypaths-task.md)  
 Vrátí odkaz na sestavení cesty různých platforem.  

 [LC – úloha](../msbuild/lc-task.md)  
 Generuje *.license* soubor *.licx* souboru.  

 [Makedir – úloha](../msbuild/makedir-task.md)  
 Vytvoří adresářů a v případě potřeby všechny nadřazené adresáře.  

 [Úloha zprávy](../msbuild/message-task.md)  
 Zaznamená zprávu během sestavení.  

 [Move – úloha](../msbuild/move-task.md)  
 Soubory přesunou do nového umístění.  

 [MSBuild – úloha](../msbuild/msbuild-task.md)  
 Sestaví [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekty z jiného [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektu.  

 [Readlinesfromfile – úloha](../msbuild/readlinesfromfile-task.md)  
 Načte seznam položek z textového souboru.  

 [Registerassembly – úloha](../msbuild/registerassembly-task.md)  
 Načte metadata v rámci zadaného sestavení a přidá nezbytné položky registru.  

 [Removedir – úloha](../msbuild/removedir-task.md)  
 Odebere zadaný adresáře a všechny jeho soubory a podadresáře.  

 [Removeduplicates – úloha](../msbuild/removeduplicates-task.md)  
 Odebere duplicitní položky z kolekce zadané položky.  

 [Requiresframework35sp1assembly – úloha](../msbuild/requiresframework35sp1assembly-task.md)  
 Určuje, zda aplikace požaduje instalaci rozhraní .NET Framework 3.5 SP1.  

 Úloha ResGen  
 Zastaralé. Použití [generateresource – úloha](../msbuild/generateresource-task.md) úloh pro převod *.txt* a *RESX* soubory do a ze společného jazykového modulu runtime binární *.resources* soubory.  

 [Resolveassemblyreference – úloha](../msbuild/resolveassemblyreference-task.md)  
 Určuje všechna sestavení, které jsou závislé na zadaná sestavení.  

 [Resolvecomreference – úloha](../msbuild/resolvecomreference-task.md)  
 Přebírá seznam jednoho nebo více typů názvy knihoven nebo *.tlb* soubory a řeší tyto knihovny typů do umístění na disku.  

 [Resolvekeysource – úloha](../msbuild/resolvekeysource-task.md)  
 Určuje zdroj klíče silného názvu  

 [Resolvemanifestfiles – úloha](../msbuild/resolvemanifestfiles-task.md)  
 Řeší následující položky v procesu sestavení k souborům pro generování manifestu: vytvořené položky, závislosti, satelity, obsah, symboly ladění a dokumentaci.  

 [Resolvenativereference – úloha](../msbuild/resolvenativereference-task.md)  
 Nativní odkazy řeší.  

 [Resolvenonmsbuildprojectoutput – úloha](../msbuild/resolvenonmsbuildprojectoutput-task.md)  
 Určuje výstupní soubory pro odkazy na projekt bez MSBuild.  

 [SGen – úloha](../msbuild/sgen-task.md)  
 Vytvoří sestavení serializace XML pro typy v zadaném sestavení.  

 [Signfile – úloha](../msbuild/signfile-task.md)  
 Zaregistruje zadaného souboru pomocí zadaného certifikátu.  

 [Touch – úloha](../msbuild/touch-task.md)  
 Nastaví dobu přístup a úpravy souborů.  

 [Unregisterassembly – úloha](../msbuild/unregisterassembly-task.md)  
 Zruší registraci zadaného sestavení pro účely vzájemné spolupráce COM.  

 [Rozbalte úloh](../msbuild/unzip-task.md)  
 Unzips *ZIP* archivní úrovně do zadaného umístění.

 [Updatemanifest – úloha](../msbuild/updatemanifest-task.md)  
 Aktualizace vybraných vlastností v manifestu a vzdává.  

 [Vbc – úloha](../msbuild/vbc-task.md)  
 Vyvolá kompilátor jazyka Visual Basic vytvoří spustitelné soubory, knihovny DLL nebo moduly kódu...  

 [Warning – úloha](../msbuild/warning-task.md)  
 Protokoly upozornění během sestavení podle Vyhodnocená podmíněném příkazu.  

 [Writecodefragment – úloha](../msbuild/writecodefragment-task.md)  
 Generuje soubor kódu dočasný pomocí fragmentu generovaného kódu. Nedojde k odstranění souboru.  

 [Writelinestofile – úloha](../msbuild/writelinestofile-task.md)  
 Zapíše zadaných položek do zadaného textového souboru.  

 [Xmlpeek – úloha](../msbuild/xmlpeek-task.md)  
 Vrací hodnoty podle specifikace dotazu XPath ze souboru XML.  

 [Xmlpoke – úloha](../msbuild/xmlpoke-task.md)  
 Nastaví hodnoty podle specifikace dotazu XPath do souboru XML.  

 [Xsltransformation – úloha](../msbuild/xsltransformation-task.md)  
 Transformuje vstupní XML pomocí *Extensible transformaci šablony stylů jazyk* (XSLT) nebo kompilované XSLT a výstupů na zařízení s výstupní soubor nebo soubor.  

  [ZipDirectory úkolu](../msbuild/zipdirectory-task.md)  
 Vytvoří *ZIP* archiv z obsah adresáře.

## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)   
 [Zápis úloh](../msbuild/task-writing.md)   
 [Úlohy](../msbuild/msbuild-tasks.md)