---
title: Úloha AL (Assembly Linker) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6861fee8691c32415111347ab673f9e48bfb9e11
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634588"
---
# <a name="al-assembly-linker-task"></a>Úloha AL (Assembly Linker)

Úloha AL zabalí *al.exe*, nástroj, který je distribuován s Windows Software Development Kit (SDK). Tento nástroj propojovací modul sestavení se používá k vytvoření sestavení s manifestem z jednoho nebo více souborů, které jsou moduly nebo soubory prostředků. Kompilátory a vývojová prostředí již mohou poskytovat tyto možnosti, takže často není nutné používat tuto úlohu přímo. Propojovací služba sestavení je nejužitečnější pro vývojáře, kteří potřebují vytvořit jedno sestavení z více souborů součástí, například ty, které mohou být vytvořeny z vývoje smíšeného jazyka. Tato úloha nekombinuje moduly do jednoho souboru sestavení; jednotlivé moduly musí být stále distribuovány a k dispozici, aby se výsledná sestava mohla správně načíst. Další informace o *souboru AL.exe*naleznete v [tématu Al.exe (Assembly Linker).](/dotnet/framework/tools/al-exe-assembly-linker)

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `AL` úkolu.

| Parametr | Popis |
|---------------------| - |
| `AlgorithmID` | Volitelný `String` parametr.<br /><br /> Určuje algoritmus, který vytvoří hodnotu hash pro všechny soubory ve vícesouborovém sestavení s výjimkou souboru, který obsahuje manifest sestavení. Další informace naleznete v dokumentaci k možnosti v `/algid` [souboru Al.exe (Assembly Linker).](/dotnet/framework/tools/al-exe-assembly-linker) |
| `BaseAddress` | Volitelný `String` parametr.<br /><br /> Určuje adresu, na kterou budou v počítači uživatele za běhu načteny knihovny DLL. Aplikace se načítají rychleji, pokud zadáte základní adresu knihoven DLL, místo toho, aby operační systém přemístil knihovny DLL v prostoru procesu. Tento parametr odpovídá adrese[/base](/dotnet/framework/tools/al-exe-assembly-linker). |
| `CompanyName` | Volitelný `String` parametr.<br /><br /> Určuje řetězec pro `Company` pole v sestavě. Další informace naleznete v dokumentaci k možnosti v `/comp[any]` [souboru Al.exe (Assembly Linker).](/dotnet/framework/tools/al-exe-assembly-linker) |
| `Configuration` | Volitelný `String` parametr.<br /><br /> Určuje řetězec pro `Configuration` pole v sestavě. Další informace naleznete v dokumentaci k možnosti v `/config[uration]` [souboru Al.exe (Assembly Linker).](/dotnet/framework/tools/al-exe-assembly-linker) |
| `Copyright` | Volitelný `String` parametr.<br /><br /> Určuje řetězec pro `Copyright` pole v sestavě. Další informace naleznete v dokumentaci k možnosti v `/copy[right]` [souboru Al.exe (Assembly Linker).](/dotnet/framework/tools/al-exe-assembly-linker) |
| `Culture` | Volitelný `String` parametr.<br /><br /> Určuje řetězec jazykové verze přidružený k sestavení. Další informace naleznete v dokumentaci k možnosti v `/c[ulture]` [souboru Al.exe (Assembly Linker).](/dotnet/framework/tools/al-exe-assembly-linker) |
| `DelaySign` | Volitelný `Boolean` parametr.<br /><br /> `true`umístit do sestavy pouze veřejný klíč; `false` k úplnému podepsání sestavy. Další informace naleznete v dokumentaci k možnosti v `/delay[sign]` [souboru Al.exe (Assembly Linker).](/dotnet/framework/tools/al-exe-assembly-linker) |
| `Description` | Volitelný `String` parametr.<br /><br /> Určuje řetězec pro `Description` pole v sestavě. Další informace naleznete v dokumentaci k možnosti v `/descr[iption]` [souboru Al.exe (Assembly Linker).](/dotnet/framework/tools/al-exe-assembly-linker) |
| `EmbedResources` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Vloží zadané prostředky do bitové kopie, která obsahuje manifest sestavení. Tento úkol zkopíruje obsah souboru prostředků do obrazu. Položky předané do tohoto parametru mohou mít `LogicalName` volitelná metadata, která jsou k nim připojena, a `Access`. Metadata `LogicalName` se používá k určení vnitřníidentifikátor pro prostředek.  Metadata `Access` lze nastavit `private` tak, aby prostředek nebyl viditelný pro jiná sestavení. Další informace naleznete v dokumentaci k možnosti v `/embed[resource]` [souboru Al.exe (Assembly Linker).](/dotnet/framework/tools/al-exe-assembly-linker) |
| `EvidenceFile` | Volitelný `String` parametr.<br /><br /> Vloží zadaný soubor do sestavení s `Security.Evidence`názvem prostředku aplikace .<br /><br /> Nelze použít `Security.Evidence` pro běžné prostředky. Tento parametr odpovídá `/e[vidence]` možnosti v [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ExitCode` | Volitelný `Int32` výstupní parametr jen pro čtení.<br /><br /> Určuje ukončovací kód poskytnutý spuštěným příkazem. |
| `FileVersion` | Volitelný `String` parametr.<br /><br /> Určuje řetězec pro `File Version` pole v sestavě. Další informace naleznete v dokumentaci k možnosti v `/fileversion` [souboru Al.exe (Assembly Linker).](/dotnet/framework/tools/al-exe-assembly-linker) |
| `Flags` | Volitelný `String` parametr.<br /><br /> Určuje hodnotu `Flags` pole v sestavě. Další informace naleznete v dokumentaci k možnosti v `/flags` [souboru Al.exe (Assembly Linker).](/dotnet/framework/tools/al-exe-assembly-linker) |
| `GenerateFullPaths` | Volitelný `Boolean` parametr.<br /><br /> Způsobí, že úloha použít absolutní cestu pro všechny soubory, které jsou hlášeny v chybové zprávě. Tento parametr odpovídá `/fullpaths` možnosti v [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `KeyContainer` | Volitelný `String` parametr.<br /><br /> Určuje kontejner obsahující pár klíčů. Toto podepíše sestavení (dá sestavení silný název) tak, že vloží veřejný klíč do manifestu sestavení. Úkol pak podepíše konečné sestavení pomocí soukromého klíče. Další informace naleznete v dokumentaci k možnosti v `/keyn[ame]` [souboru Al.exe (Assembly Linker).](/dotnet/framework/tools/al-exe-assembly-linker) |
| `KeyFile` | Volitelný `String` parametr.<br /><br /> Určuje soubor, který obsahuje dvojici klíčů nebo pouze veřejný klíč k podepsání sestavení. Kompilátor vloží veřejný klíč do manifestu sestavení a poté podepíše konečné sestavení soukromým klíčem. Další informace naleznete v dokumentaci k možnosti v `/keyf[ile]` [souboru Al.exe (Assembly Linker).](/dotnet/framework/tools/al-exe-assembly-linker) |
| `LinkResources` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Propojí zadané soubory prostředků se sestavením. Prostředek se stane součástí sestavení, ale soubor není zkopírován. Položky předané tomuto parametru mohou mít volitelná metadata s názvem `LogicalName`, `Target`, a `Access`. Metadata `LogicalName` se používá k určení vnitřníidentifikátor pro prostředek. Metadata `Target` můžete určit cestu a název souboru, do kterého úkol zkopíruje soubor, po kterém zkompiluje tento nový soubor do sestavení. Metadata `Access` lze nastavit `private` tak, aby prostředek nebyl viditelný pro jiná sestavení. Další informace naleznete v dokumentaci k možnosti v `/link[resource]` [souboru Al.exe (Assembly Linker).](/dotnet/framework/tools/al-exe-assembly-linker) |
| `MainEntryPoint` | Volitelný `String` parametr.<br /><br /> Určuje plně kvalifikovaný název *(class.method)* metody, která má být používána jako vstupní bod při převodu modulu na spustitelný soubor. Tento parametr odpovídá `/main` možnosti v [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `OutputAssembly` | Požadovaný <xref:Microsoft.Build.Framework.ITaskItem> výstupní parametr.<br /><br /> Určuje název souboru generovaného touto úlohou. Tento parametr odpovídá `/out` možnosti v [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Platform` | Volitelný `String` parametr.<br /><br /> Omezuje platformu, na které může tento kód běžet; musí být `x86`jedním `Itanium` `x64`z `anycpu`, , , nebo . Výchozí formát je `anycpu`. Tento parametr odpovídá `/platform` možnosti v [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ProductName` | Volitelný `String` parametr.<br /><br /> Určuje řetězec pro `Product` pole v sestavě. Další informace naleznete v dokumentaci k možnosti v `/prod[uct]` [souboru Al.exe (Assembly Linker).](/dotnet/framework/tools/al-exe-assembly-linker) |
| `ProductVersion` | Volitelný `String` parametr.<br /><br /> Určuje řetězec pro `ProductVersion` pole v sestavě. Další informace naleznete v dokumentaci k možnosti v `/productv[ersion]` [souboru Al.exe (Assembly Linker).](/dotnet/framework/tools/al-exe-assembly-linker) |
| `ResponseFiles` | Volitelný `String[]` parametr.<br /><br /> Určuje soubory odpovědí, které obsahují další možnosti pro průchod do propojovacího systému sestavení. |
| `SdkToolsPath` | Volitelný `String` parametr.<br /><br /> Určuje cestu k nástrojům sady SDK, například resgen.exe. |
| `SourceModules` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Jeden nebo více modulů, které mají být zkompilovány do sestavení. Moduly budou uvedeny v manifestu výsledné sestavy a budou stále muset být distribuovány a k dispozici, aby se sestava načetla. Položky předané do tohoto parametru `Target`mohou mít další metadata s názvem , který určuje cestu a název souboru, do kterého úkol zkopíruje soubor, po kterém zkompiluje tento nový soubor do sestavení. Další informace naleznete v dokumentaci k [souboru Al.exe (Assembly Linker).](/dotnet/framework/tools/al-exe-assembly-linker) Tento parametr odpovídá seznamu modulů předaných do *al.exe* bez specifického přepínače. |
| `TargetType` | Volitelný `String` parametr.<br /><br /> Určuje formát souboru výstupního `library` souboru: `exe` (knihovna kódu), (konzolová aplikace) nebo `win` (aplikace založená na systému Windows). Výchozí formát je `library`. Tento parametr odpovídá `/t[arget]` možnosti v [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `TemplateFile` | Volitelný `String` parametr.<br /><br /> Určuje sestavení, ze kterého mají dědit všechna metadata sestavení, s výjimkou pole jazykové verze. Zadané sestavení musí mít silný název.<br /><br /> Sestavení, které vytvoříte `TemplateFile` s parametrem bude satelitní sestavení. Tento parametr odpovídá `/template` možnosti v [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Timeout` | Volitelný `Int32` parametr.<br /><br /> Určuje dobu v milisekundách, po jejímž uplynutí je spustitelný soubor úlohy ukončen. Výchozí hodnota `Int.MaxValue`je , označující, že neexistuje žádné časové období. |
| `Title` | Volitelný `String` parametr.<br /><br /> Určuje řetězec pro `Title` pole v sestavě. Další informace naleznete v dokumentaci k možnosti v `/title` [souboru Al.exe (Assembly Linker).](/dotnet/framework/tools/al-exe-assembly-linker) |
| `ToolPath` | Volitelný `String` parametr.<br /><br /> Určuje umístění, ze kterého bude úloha načíst základní spustitelný soubor (Al.exe). Pokud tento parametr není zadán, úloha používá instalační cestu sady SDK odpovídající verzi rozhraní, ve které je spuštěno službu MSBuild. |
| `Trademark` | Volitelný `String` parametr.<br /><br /> Určuje řetězec pro `Trademark` pole v sestavě. Další informace naleznete v dokumentaci k možnosti v `/trade[mark]` [souboru Al.exe (Assembly Linker).](/dotnet/framework/tools/al-exe-assembly-linker) |
| `Version` | Volitelný `String` parametr.<br /><br /> Určuje informace o verzi pro toto sestavení. Formát řetězce je *major.minor.build.revision*. Výchozí hodnota je 0. Další informace naleznete v dokumentaci k možnosti v `/v[ersion]` [souboru Al.exe (Assembly Linker).](/dotnet/framework/tools/al-exe-assembly-linker) |
| `Win32Icon` | Volitelný `String` parametr.<br /><br /> Vloží soubor *ICO* do sestavy. Soubor *.ico* poskytuje výstupnímu souboru požadovaný vzhled v Průzkumníkovi souborů. Tento parametr odpovídá `/win32icon` možnosti v [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Win32Resource` | Volitelný `String` parametr.<br /><br /> Vloží do výstupního souboru prostředek Win32 (*soubor res).* Další informace naleznete v dokumentaci k možnosti v `/win32res` [souboru Al.exe (Assembly Linker).](/dotnet/framework/tools/al-exe-assembly-linker) |

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.ToolTaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.ToolTask> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [ToolTaskExtension base class](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad vytvoří sestavení se zadanými možnostmi.

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

## <a name="see-also"></a>Viz také

* [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
* [Úlohy](../msbuild/msbuild-tasks.md)
