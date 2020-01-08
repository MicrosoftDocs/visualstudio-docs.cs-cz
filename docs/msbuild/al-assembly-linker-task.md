---
title: AL (linker sestavení) – úloha | Microsoft Docs
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
ms.openlocfilehash: d90e6c94d07b73e79d793982944bca395a562df2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593470"
---
# <a name="al-assembly-linker-task"></a>AL (Assembly Linker) – úloha
Úloha AL zalomí *Al. exe*, který je distribuován s [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Tento nástroj Assembly Linker slouží k vytvoření sestavení s manifestem z jednoho nebo více souborů, které jsou buď moduly, nebo soubory prostředků. Kompilátory a vývojová prostředí mohou již tyto možnosti poskytovat, takže často není nutné tuto úlohu používat přímo. Linker sestavení je nejužitečnější vývojářům, kteří potřebují vytvořit jedno sestavení z více souborů komponenty, jako jsou například ty, které mohou být vytvořeny z vývoje smíšeného jazyka. Tato úloha nespojuje moduly do jednoho souboru sestavení; aby se výsledné sestavení správně načetlo, musí být jednotlivé moduly stále distribuované a dostupné. Další informace o *Al. exe*naleznete v tématu [Al. exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).

## <a name="parameters"></a>Parametry
 Následující tabulka popisuje parametry úlohy `AL`.

| Parametr | Popis |
|---------------------| - |
| `AlgorithmID` | Volitelný parametr `String`.<br /><br /> Určuje algoritmus, který vytvoří hodnotu hash pro všechny soubory ve vícesouborovém sestavení s výjimkou souboru, který obsahuje manifest sestavení. Další informace naleznete v dokumentaci k možnosti `/algid` v [Al. exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `BaseAddress` | Volitelný parametr `String`.<br /><br /> Určuje adresu, na kterou budou v počítači uživatele za běhu načteny knihovny DLL. Aplikace se načítají rychleji, pokud zadáte základní adresu knihoven DLL, namísto toho, aby operační systém přemístění knihoven DLL v prostoru procesu. Tento parametr odpovídá[adrese](/dotnet/framework/tools/al-exe-assembly-linker)/Base. |
| `CompanyName` | Volitelný parametr `String`.<br /><br /> Určuje řetězec pro pole `Company` v sestavení. Další informace naleznete v dokumentaci k možnosti `/comp[any]` v [Al. exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Configuration` | Volitelný parametr `String`.<br /><br /> Určuje řetězec pro pole `Configuration` v sestavení. Další informace naleznete v dokumentaci k možnosti `/config[uration]` v [Al. exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Copyright` | Volitelný parametr `String`.<br /><br /> Určuje řetězec pro pole `Copyright` v sestavení. Další informace naleznete v dokumentaci k možnosti `/copy[right]` v [Al. exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Culture` | Volitelný parametr `String`.<br /><br /> Určuje řetězec jazykové verze přidružený k sestavení. Další informace naleznete v dokumentaci k možnosti `/c[ulture]` v [Al. exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `DelaySign` | Volitelný parametr `Boolean`.<br /><br /> `true` umístit pouze veřejný klíč do sestavení; `false` pro úplné podepsání sestavení. Další informace naleznete v dokumentaci k možnosti `/delay[sign]` v [Al. exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Description` | Volitelný parametr `String`.<br /><br /> Určuje řetězec pro pole `Description` v sestavení. Další informace naleznete v dokumentaci k možnosti `/descr[iption]` v [Al. exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `EmbedResources` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Vloží zadané prostředky do bitové kopie, která obsahuje manifest sestavení. Tento úkol zkopíruje obsah souboru prostředků do bitové kopie. K položkám předaným do tohoto parametru můžou být připojená volitelná metadata, která se nazývají `LogicalName` a `Access`. Metadata `LogicalName` se používají k určení interního identifikátoru prostředku.  Metadata `Access` lze nastavit na `private`, aby bylo možné prostředek zviditelnit jiným sestavením. Další informace naleznete v dokumentaci k možnosti `/embed[resource]` v [Al. exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `EvidenceFile` | Volitelný parametr `String`.<br /><br /> Vloží zadaný soubor do sestavení s názvem prostředku `Security.Evidence`.<br /><br /> Pro běžné prostředky nemůžete použít `Security.Evidence`. Tento parametr odpovídá možnosti `/e[vidence]` v [Al. exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ExitCode` | Volitelný `Int32` výstupní parametr jen pro čtení.<br /><br /> Určuje ukončovací kód poskytnutý spuštěným příkazem. |
| `FileVersion` | Volitelný parametr `String`.<br /><br /> Určuje řetězec pro pole `File Version` v sestavení. Další informace naleznete v dokumentaci k možnosti `/fileversion` v [Al. exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Flags` | Volitelný parametr `String`.<br /><br /> Určuje hodnotu pro pole `Flags` v sestavení. Další informace naleznete v dokumentaci k možnosti `/flags` v [Al. exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `GenerateFullPaths` | Volitelný parametr `Boolean`.<br /><br /> Způsobí, že úkol použije absolutní cestu pro všechny soubory, které jsou uvedeny v chybové zprávě. Tento parametr odpovídá možnosti `/fullpaths` v [Al. exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `KeyContainer` | Volitelný parametr `String`.<br /><br /> Určuje kontejner obsahující pár klíčů. Toto podepíše sestavení (dá sestavení silný název) tak, že vloží veřejný klíč do manifestu sestavení. Úloha pak podepíše konečné sestavení pomocí privátního klíče. Další informace naleznete v dokumentaci k možnosti `/keyn[ame]` v [Al. exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `KeyFile` | Volitelný parametr `String`.<br /><br /> Určuje soubor, který obsahuje dvojici klíčů nebo pouze veřejný klíč pro podepsání sestavení. Kompilátor vloží veřejný klíč do manifestu sestavení a poté podepíše konečné sestavení soukromým klíčem. Další informace naleznete v dokumentaci k možnosti `/keyf[ile]` v [Al. exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `LinkResources` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Propojí zadané soubory prostředků se sestavením. Prostředek se stal součástí sestavení, ale soubor se nezkopíruje. K položkám předaným do tohoto parametru můžou být připojená volitelná metadata, která se nazývají `LogicalName`, `Target`a `Access`. Metadata `LogicalName` se používají k určení interního identifikátoru prostředku. `Target` metadata lze zadat cestu a název souboru, do kterého úloha kopíruje soubor, poté zkompiluje tento nový soubor do sestavení. Metadata `Access` lze nastavit na `private`, aby bylo možné prostředek zviditelnit jiným sestavením. Další informace naleznete v dokumentaci k možnosti `/link[resource]` v [Al. exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `MainEntryPoint` | Volitelný parametr `String`.<br /><br /> Určuje plně kvalifikovaný název (*Class. Method*) metody, která se má použít jako vstupní bod při převodu modulu na spustitelný soubor. Tento parametr odpovídá možnosti `/main` v [Al. exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `OutputAssembly` | Požadovaný výstupní parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje název souboru vygenerovaného tímto úkolem. Tento parametr odpovídá možnosti `/out` v [Al. exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Platform` | Volitelný parametr `String`.<br /><br /> Omezuje platformu, na které se tento kód může spustit; musí se jednat o jednu z `x86`, `Itanium`, `x64`nebo `anycpu`. Výchozí hodnota je `anycpu`. Tento parametr odpovídá možnosti `/platform` v [Al. exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ProductName` | Volitelný parametr `String`.<br /><br /> Určuje řetězec pro pole `Product` v sestavení. Další informace naleznete v dokumentaci k možnosti `/prod[uct]` v [Al. exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ProductVersion` | Volitelný parametr `String`.<br /><br /> Určuje řetězec pro pole `ProductVersion` v sestavení. Další informace naleznete v dokumentaci k možnosti `/productv[ersion]` v [Al. exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ResponseFiles` | Volitelný parametr `String[]`.<br /><br /> Určuje soubory odezvy, které obsahují další možnosti, které mají být před linkerem sestavení předávány. |
| `SdkToolsPath` | Volitelný parametr `String`.<br /><br /> Určuje cestu k nástrojům sady SDK, jako je Resgen. exe. |
| `SourceModules` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Jeden nebo více modulů, které mají být zkompilovány do sestavení. Moduly budou uvedeny v manifestu výsledného sestavení a bude stále muset být distribuován a k dispozici, aby bylo sestavení načteno. Položky předané do tohoto parametru mohou mít další metadata s názvem `Target`, která určuje cestu a název souboru, do kterého úloha kopíruje soubor, poté zkompiluje tento nový soubor do sestavení. Další informace naleznete v dokumentaci k nástroji [Al. exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). Tento parametr odpovídá seznamu modulů předaných do souboru *Al. exe* bez konkrétního přepínače. |
| `TargetType` | Volitelný parametr `String`.<br /><br /> Určuje formát výstupního souboru: `library` (knihovna kódu), `exe` (Konzolová aplikace) nebo `win` (aplikace založené na systému Windows). Výchozí hodnota je `library`. Tento parametr odpovídá možnosti `/t[arget]` v [Al. exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `TemplateFile` | Volitelný parametr `String`.<br /><br /> Určuje sestavení, ze kterého mají být děděna všechna metadata sestavení, s výjimkou pole culture. Zadané sestavení musí mít silný název.<br /><br /> Sestavení, které vytvoříte s parametrem `TemplateFile`, bude satelitní sestavení. Tento parametr odpovídá možnosti `/template` v [Al. exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Timeout` | Volitelný parametr `Int32`.<br /><br /> Určuje dobu v milisekundách, po jejímž uplynutí je ukončen spustitelný soubor úlohy. Výchozí hodnota je `Int.MaxValue`, což značí, že není k dispozici žádný časový interval. |
| `Title` | Volitelný parametr `String`.<br /><br /> Určuje řetězec pro pole `Title` v sestavení. Další informace naleznete v dokumentaci k možnosti `/title` v [Al. exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ToolPath` | Volitelný parametr `String`.<br /><br /> Určuje umístění, ze kterého bude úloha načítat základní spustitelný soubor (Al. exe). Pokud tento parametr není zadán, úloha použije cestu instalace sady SDK odpovídající verzi rozhraní .NET Framework, která je spuštěna [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |
| `Trademark` | Volitelný parametr `String`.<br /><br /> Určuje řetězec pro pole `Trademark` v sestavení. Další informace naleznete v dokumentaci k možnosti `/trade[mark]` v [Al. exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Version` | Volitelný parametr `String`.<br /><br /> Určuje informace o verzi pro toto sestavení. Formát řetězce je *hlavní_verze. podverze. sestavení. revize*. Výchozí hodnota je 0. Další informace naleznete v dokumentaci k možnosti `/v[ersion]` v [Al. exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Win32Icon` | Volitelný parametr `String`.<br /><br /> Vloží soubor *. ico* do sestavení. Soubor *. ico* poskytne výstupnímu souboru požadovaný vzhled v Průzkumníkovi souborů. Tento parametr odpovídá možnosti `/win32icon` v [Al. exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Win32Resource` | Volitelný parametr `String`.<br /><br /> Vloží prostředek systému Win32 (soubor *. res* ) do výstupního souboru. Další informace naleznete v dokumentaci k možnosti `/win32res` v [Al. exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |

## <a name="remarks"></a>Poznámky
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.ToolTask> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [ToolTaskExtension – Base Class](../msbuild/tooltaskextension-base-class.md).

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

## <a name="see-also"></a>Viz také:
* [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
* [Úlohy](../msbuild/msbuild-tasks.md)
