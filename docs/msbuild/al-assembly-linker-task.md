---
title: AL (Linker sestavení) úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AL
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- AL task [MSBuild]
- MSBuild, AL task
ms.assetid: 2ddefbf2-5662-4d55-99a6-ac383bf44560
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0a9c2a362a27c24daf1802482ed7a52d9f1d0f2b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49824376"
---
# <a name="al-assembly-linker-task"></a>AL (Linker sestavení) – úloha
Al – úloha zabalí *AL.exe*, nástroj, který je distribuován spolu s [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Tento nástroj Linker sestavení se používá k vytvoření sestavení s manifestem z jednoho nebo více souborů, které jsou buď moduly nebo souborů prostředků. Kompilátory a vývojová prostředí už zadat tyto možnosti tak, aby byl často není potřeba přímo pomocí této úlohy. Linker sestavení je zvláště užitečná pro vývojáře, které by bylo potřeba vytvořte jedno sestavení z více souborů součástí, například ty, které může být vytvořen z jazyků vývoj. Tato úloha není možné sloučit moduly do jednoho sestavení souboru; jednotlivé moduly musí být stále distribuované a k dispozici v pořadí pro výsledné sestavení se načíst správně. Další informace o *AL.exe*, naleznete v tématu [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker).  

## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `AL` úloh.  


| Parametr | Popis |
|---------------------| - |
| `AlgorithmID` | Volitelné `String` parametru.<br /><br /> Určuje algoritmus, který vytvoří hodnotu hash pro všechny soubory ve vícesouborovém sestavení s výjimkou souboru, který obsahuje manifest sestavení. Další informace najdete v tématu v dokumentaci `/algid` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `BaseAddress` | Volitelné `String` parametru.<br /><br /> Určuje adresu, na kterou budou v počítači uživatele za běhu načteny knihovny DLL. Aplikace se načítají rychleji při zadání základní adresy knihoven DLL, namísto dovolení operačnímu systému přemisťovat knihovny DLL v prostoru procesu. Tento parametr odpovídá propojovacího[adresu](/dotnet/framework/tools/al-exe-assembly-linker). |
| `CompanyName` | Volitelné `String` parametru.<br /><br /> Určuje řetězec pro `Company` pole v sestavení. Další informace najdete v tématu v dokumentaci `/comp[any]` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Configuration` | Volitelné `String` parametru.<br /><br /> Určuje řetězec pro `Configuration` pole v sestavení. Další informace najdete v tématu v dokumentaci `/config[uration]` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Copyright` | Volitelné `String` parametru.<br /><br /> Určuje řetězec pro `Copyright` pole v sestavení. Další informace najdete v tématu v dokumentaci `/copy[right]` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Culture` | Volitelné `String` parametru.<br /><br /> Určuje řetězec jazykové verze přidružený k sestavení. Další informace najdete v tématu v dokumentaci `/c[ulture]` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `DelaySign` | Volitelné `Boolean` parametru.<br /><br /> `true` Chcete-li umístit pouze veřejný klíč sestavení; `false` plně podepsat sestavení. Další informace najdete v tématu v dokumentaci `/delay[sign]` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Description` | Volitelné `String` parametru.<br /><br /> Určuje řetězec pro `Description` pole v sestavení. Další informace najdete v tématu v dokumentaci `/descr[iption]` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `EmbedResources` | Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Vloží zadané zdroje obrázku, který obsahuje manifest sestavení. Tato úloha zkopíruje obsah souboru prostředků do bitové kopie. Volitelná metadata připojené k je volána, mohou mít položky v předaných tomuto parametru `LogicalName` a `Access`. `LogicalName` Metadat se používá k určení interní identifikátor prostředku.  `Access` Metadat může být nastaven na `private` aby prostředku není viditelné pro jiná sestavení. Další informace najdete v tématu v dokumentaci `/embed[resource]` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `EvidenceFile` | Volitelné `String` parametru.<br /><br /> Vloží zadaný soubor v sestavení s názvem prostředku `Security.Evidence`.<br /><br /> Nemůžete použít `Security.Evidence` pro běžné prostředky. Tento parametr `/e[vidence]` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ExitCode` | Volitelné `Int32` výstupní parametr jen pro čtení.<br /><br /> Určuje ukončovací kód poskytuje provedeného příkazu. |
| `FileVersion` | Volitelné `String` parametru.<br /><br /> Určuje řetězec pro `File Version` pole v sestavení. Další informace najdete v tématu v dokumentaci `/fileversion` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Flags` | Volitelné `String` parametru.<br /><br /> Určuje hodnotu `Flags` pole v sestavení. Další informace najdete v tématu v dokumentaci `/flags` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `GenerateFullPaths` | Volitelné `Boolean` parametru.<br /><br /> Způsobí, že úkol použije absolutní cestu pro soubory, které jsou hlášeny v chybové zprávě. Tento parametr `/fullpaths` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `KeyContainer` | Volitelné `String` parametru.<br /><br /> Určuje kontejner obsahující pár klíčů. Toto podepíše sestavení (dá sestavení silný název) tak, že vloží veřejný klíč do manifestu sestavení. Úloha se pak podepíše konečné sestavení soukromým klíčem. Další informace najdete v tématu v dokumentaci `/keyn[ame]` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `KeyFile` | Volitelné `String` parametru.<br /><br /> Určuje soubor, který obsahuje pár klíčů nebo pouze veřejný klíč pro podpis sestavení. Kompilátor vloží veřejný klíč do manifestu sestavení a poté podepíše konečné sestavení soukromým klíčem. Další informace najdete v tématu v dokumentaci `/keyf[ile]` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `LinkResources` | Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Propojí určené soubory prostředků do sestavení. Prostředek se stane součástí sestavení, ale soubor nebude zkopírován. Volitelná metadata připojené k je volána, mohou mít položky v předaných tomuto parametru `LogicalName`, `Target`, a `Access`. `LogicalName` Metadat se používá k určení interní identifikátor prostředku. `Target` Metadat můžete zadat cestu a název souboru, ke kterému úkol zkopíruje soubor, po jejímž uplynutí se zkompiluje tohoto nového souboru do sestavení. `Access` Metadat může být nastaven na `private` aby prostředku není viditelné pro jiná sestavení. Další informace najdete v tématu v dokumentaci `/link[resource]` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `MainEntryPoint` | Volitelné `String` parametru.<br /><br /> Určuje plně kvalifikovaný název (*. class.method*) metody pro použití jako vstupní bod při převodu modulu na spustitelný soubor. Tento parametr `/main` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `OutputAssembly` | Vyžaduje <xref:Microsoft.Build.Framework.ITaskItem> výstupní parametr.<br /><br /> Určuje název souboru vygenerovaného touto úlohou. Tento parametr `/out` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Platform` | Volitelné `String` parametru.<br /><br /> Omezuje kterou platformu, lze tento kód spustit. musí být jedna z `x86`, `Itanium`, `x64`, nebo `anycpu`. Výchozí hodnota je `anycpu`. Tento parametr `/platform` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ProductName` | Volitelné `String` parametru.<br /><br /> Určuje řetězec pro `Product` pole v sestavení. Další informace najdete v tématu v dokumentaci `/prod[uct]` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ProductVersion` | Volitelné `String` parametru.<br /><br /> Určuje řetězec pro `ProductVersion` pole v sestavení. Další informace najdete v tématu v dokumentaci `/productv[ersion]` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ResponseFiles` | Volitelné `String[]` parametru.<br /><br /> Určuje soubory odpovědí, které obsahují další možnosti předávání do propojovacího programu sestavení. |
| `SdkToolsPath` | Volitelné `String` parametru.<br /><br /> Určuje cestu k sadě SDK nástroje, jako je resgen.exe. |
| `SourceModules` | Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Jeden nebo více modulů se zkompiluje do sestavení. Moduly budou uvedené v manifestu výsledné sestavení a stále muset distribuované a k dispozici v pořadí pro načtení sestavení. Položek předaných do tento parametr může mít další metadata, která volá `Target`, který určuje cestu a název souboru, ke kterému úkol zkopíruje soubor, po jejímž uplynutí se zkompiluje tohoto nového souboru do sestavení. Další informace najdete v dokumentaci pro [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). Tento parametr odpovídá seznamu modulů, které jsou předány do *Al.exe* bez konkrétním přepínačem. |
| `TargetType` | Volitelné `String` parametru.<br /><br /> Určuje formát výstupního souboru: `library` (kód knihovny), `exe` (konzolové aplikace), nebo `win` (aplikace založené na Windows). Výchozí hodnota je `library`. Tento parametr `/t[arget]` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `TemplateFile` | Volitelné `String` parametru.<br /><br /> Určuje sestavení, ze kterého se dědí všechna metadata sestavení s výjimkou pole jazykové verze. Zadané sestavení musí mít silný název.<br /><br /> Sestavení, které vytvoříte pomocí `TemplateFile` parametr bude satelitní sestavení. Tento parametr `/template` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Timeout` | Volitelné `Int32` parametru.<br /><br /> Určuje množství času, v milisekundách, po jejichž uplynutí je spustitelný soubor s úkolem ukončen. Výchozí hodnota je `Int.MaxValue`, která udává, že neexistuje žádný časový limit. |
| `Title` | Volitelné `String` parametru.<br /><br /> Určuje řetězec pro `Title` pole v sestavení. Další informace najdete v tématu v dokumentaci `/title` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ToolPath` | Volitelné `String` parametru.<br /><br /> Určuje umístění, kde bude úloha načtení základní spustitelného souboru (Al.exe). Pokud není tento parametr zadán, použije úloha instalační cestu sady SDK odpovídající verzi rozhraní framework, na kterém běží [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |
| `Trademark` | Volitelné `String` parametru.<br /><br /> Určuje řetězec pro `Trademark` pole v sestavení. Další informace najdete v tématu v dokumentaci `/trade[mark]` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Version` | Volitelné `String` parametru.<br /><br /> Určuje informace o verzi pro toto sestavení. Formát řetězce je *major.minor.build.revision*. Výchozí hodnota je 0. Další informace najdete v tématu v dokumentaci `/v[ersion]` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Win32Icon` | Volitelné `String` parametru.<br /><br /> Vloží *.ico* soubor sestavení. *.Ico* souboru dává výstupnímu souboru požadovaný vzhled v Průzkumníku souborů. Tento parametr `/win32icon` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Win32Resource` | Volitelné `String` parametru.<br /><br /> Vloží prostředek systému Win32 (*.res* soubor) do výstupního souboru. Další informace najdete v tématu v dokumentaci `/win32res` možnost [Al.exe (Linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |

## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.ToolTaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.ToolTask> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [tooltaskextension – základní třída](../msbuild/tooltaskextension-base-class.md).  

## <a name="example"></a>Příklad  
 Následující příklad vytvoří sestavení s konkrétní možnosti.  

```xml  
<AL  
    EmbedResources="@(EmbeddedResource)"  
    Culture="%(EmbeddedResource.Culture)"  
    TemplateFile="@(IntermediateAssembly)"  
    KeyContainer="$(KeyContainerName)"  
    KeyFile="$(KeyOriginatorFile)"  
    DelaySign="$(DelaySign)"  

    OutputAssembly=  
       "%(EmbeddedResource.Culture)\$(TargetName).resources.dll">  

    <Output TaskParameter="OutputAssembly"  
        ItemName="SatelliteAssemblies"/>  
</AL>  
```  

## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)   
 [Úlohy](../msbuild/msbuild-tasks.md)