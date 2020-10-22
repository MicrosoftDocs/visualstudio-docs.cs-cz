---
title: AL (linker sestavení) – úloha | Microsoft Docs
description: Použijte úlohu linker Assembly Linker (AL) k zabalení AL.exe, nástroje, který je distribuován pomocí sady Windows Software Development Kit.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: d59251240abc7ca39b3819adf2324bf5bb9cef0a
ms.sourcegitcommit: d3bca34f82de03fa34ecdd72233676c17fb3cb14
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2020
ms.locfileid: "92353353"
---
# <a name="al-assembly-linker-task"></a>AL (linker sestavení) – úloha

Úkol AL se zalomí *AL.exe*, nástroj, který je distribuován pomocí sady Windows Software Development Kit (SDK). Tento nástroj Assembly Linker slouží k vytvoření sestavení s manifestem z jednoho nebo více souborů, které jsou buď moduly, nebo soubory prostředků. Kompilátory a vývojová prostředí mohou již tyto možnosti poskytovat, takže často není nutné tuto úlohu používat přímo. Linker sestavení je nejužitečnější vývojářům, kteří potřebují vytvořit jedno sestavení z více souborů komponenty, jako jsou například ty, které mohou být vytvořeny z vývoje smíšeného jazyka. Tato úloha nespojuje moduly do jednoho souboru sestavení; aby se výsledné sestavení správně načetlo, musí být jednotlivé moduly stále distribuované a dostupné. Další informace o *AL.exe*naleznete v tématu [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker).

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `AL` úkolu.

| Parametr | Popis |
|---------------------| - |
| `AlgorithmID` | Volitelný `String` parametr.<br /><br /> Určuje algoritmus, který vytvoří hodnotu hash pro všechny soubory ve vícesouborovém sestavení s výjimkou souboru, který obsahuje manifest sestavení. Další informace naleznete v dokumentaci k `/algid` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `BaseAddress` | Volitelný `String` parametr.<br /><br /> Určuje adresu, na kterou budou v počítači uživatele za běhu načteny knihovny DLL. Aplikace se načítají rychleji, pokud zadáte základní adresu knihoven DLL, namísto toho, aby operační systém přemístění knihoven DLL v prostoru procesu. Tento parametr odpovídá[adrese](/dotnet/framework/tools/al-exe-assembly-linker)/Base. |
| `CompanyName` | Volitelný `String` parametr.<br /><br /> Určuje řetězec pro `Company` pole v sestavení. Další informace naleznete v dokumentaci k `/comp[any]` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Configuration` | Volitelný `String` parametr.<br /><br /> Určuje řetězec pro `Configuration` pole v sestavení. Další informace naleznete v dokumentaci k `/config[uration]` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Copyright` | Volitelný `String` parametr.<br /><br /> Určuje řetězec pro `Copyright` pole v sestavení. Další informace naleznete v dokumentaci k `/copy[right]` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Culture` | Volitelný `String` parametr.<br /><br /> Určuje řetězec jazykové verze přidružený k sestavení. Další informace naleznete v dokumentaci k `/c[ulture]` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `DelaySign` | Volitelný `Boolean` parametr.<br /><br /> `true` Chcete-li umístit pouze veřejný klíč do sestavení; `false` pro úplné podepsání sestavení. Další informace naleznete v dokumentaci k `/delay[sign]` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Description` | Volitelný `String` parametr.<br /><br /> Určuje řetězec pro `Description` pole v sestavení. Další informace naleznete v dokumentaci k `/descr[iption]` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `EmbedResources` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Vloží zadané prostředky do bitové kopie, která obsahuje manifest sestavení. Tento úkol zkopíruje obsah souboru prostředků do bitové kopie. K položkám předaným do tohoto parametru mohou být připojena volitelná metadata, která jsou volána `LogicalName` a `Access` . `LogicalName`Metadata se používají k určení interního identifikátoru prostředku.  `Access`Metadata lze nastavit na hodnotu, aby bylo možné `private` prostředek zviditelnit jiným sestavením. Další informace naleznete v dokumentaci k `/embed[resource]` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `EvidenceFile` | Volitelný `String` parametr.<br /><br /> Vloží zadaný soubor do sestavení s názvem prostředku `Security.Evidence` .<br /><br /> Nemůžete použít `Security.Evidence` pro běžné prostředky. Tento parametr odpovídá `/e[vidence]` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ExitCode` | Volitelný `Int32` výstup – parametr jen pro čtení.<br /><br /> Určuje ukončovací kód poskytnutý spuštěným příkazem. |
| `FileVersion` | Volitelný `String` parametr.<br /><br /> Určuje řetězec pro `File Version` pole v sestavení. Další informace naleznete v dokumentaci k `/fileversion` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Flags` | Volitelný `String` parametr.<br /><br /> Určuje hodnotu pro `Flags` pole v sestavení. Další informace naleznete v dokumentaci k `/flags` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `GenerateFullPaths` | Volitelný `Boolean` parametr.<br /><br /> Způsobí, že úkol použije absolutní cestu pro všechny soubory, které jsou uvedeny v chybové zprávě. Tento parametr odpovídá `/fullpaths` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `KeyContainer` | Volitelný `String` parametr.<br /><br /> Určuje kontejner obsahující pár klíčů. Toto podepíše sestavení (dá sestavení silný název) tak, že vloží veřejný klíč do manifestu sestavení. Úloha pak podepíše konečné sestavení pomocí privátního klíče. Další informace naleznete v dokumentaci k `/keyn[ame]` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `KeyFile` | Volitelný `String` parametr.<br /><br /> Určuje soubor, který obsahuje dvojici klíčů nebo pouze veřejný klíč pro podepsání sestavení. Kompilátor vloží veřejný klíč do manifestu sestavení a poté podepíše konečné sestavení soukromým klíčem. Další informace naleznete v dokumentaci k `/keyf[ile]` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `LinkResources` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Propojí zadané soubory prostředků se sestavením. Prostředek se stal součástí sestavení, ale soubor se nezkopíruje. K položkám předaným do tohoto parametru mohou být připojena volitelná metadata, která jsou volána `LogicalName` , `Target` a `Access` . `LogicalName`Metadata se používají k určení interního identifikátoru prostředku. `Target`Metadata mohou určovat cestu a název souboru, do kterého úloha kopíruje soubor, poté zkompiluje tento nový soubor do sestavení. `Access`Metadata lze nastavit na hodnotu, aby bylo možné `private` prostředek zviditelnit jiným sestavením. Další informace naleznete v dokumentaci k `/link[resource]` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `MainEntryPoint` | Volitelný `String` parametr.<br /><br /> Určuje plně kvalifikovaný název (*Class. Method*) metody, která se má použít jako vstupní bod při převodu modulu na spustitelný soubor. Tento parametr odpovídá `/main` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `OutputAssembly` | Vyžaduje se <xref:Microsoft.Build.Framework.ITaskItem> výstupní parametr.<br /><br /> Určuje název souboru vygenerovaného tímto úkolem. Tento parametr odpovídá `/out` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Platform` | Volitelný `String` parametr.<br /><br /> Omezuje platformu, na které se tento kód může spustit; musí být jedním z `x86` , `Itanium` , `x64` nebo `anycpu` . Výchozí formát je `anycpu`. Tento parametr odpovídá `/platform` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ProductName` | Volitelný `String` parametr.<br /><br /> Určuje řetězec pro `Product` pole v sestavení. Další informace naleznete v dokumentaci k `/prod[uct]` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ProductVersion` | Volitelný `String` parametr.<br /><br /> Určuje řetězec pro `ProductVersion` pole v sestavení. Další informace naleznete v dokumentaci k `/productv[ersion]` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ResponseFiles` | Volitelný `String[]` parametr.<br /><br /> Určuje soubory odezvy, které obsahují další možnosti, které mají být před linkerem sestavení předávány. |
| `SdkToolsPath` | Volitelný `String` parametr.<br /><br /> Určuje cestu k nástrojům sady SDK, jako je například resgen.exe. |
| `SourceModules` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Jeden nebo více modulů, které mají být zkompilovány do sestavení. Moduly budou uvedeny v manifestu výsledného sestavení a bude stále muset být distribuován a k dispozici, aby bylo sestavení načteno. K položkám předaným do tohoto parametru mohou být volána další metadata `Target` , která určují cestu a název souboru, do kterého úloha kopíruje soubor, poté zkompiluje tento nový soubor do sestavení. Další informace naleznete v dokumentaci pro [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). Tento parametr odpovídá seznamu modulů předaných do *Al.exe* bez konkrétního přepínače. |
| `TargetType` | Volitelný `String` parametr.<br /><br /> Určuje formát výstupního souboru: `library` (knihovna kódu), `exe` (Konzolová aplikace) nebo `win` (aplikace založená na systému Windows). Výchozí formát je `library`. Tento parametr odpovídá `/t[arget]` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `TemplateFile` | Volitelný `String` parametr.<br /><br /> Určuje sestavení, ze kterého mají být děděna všechna metadata sestavení, s výjimkou pole culture. Zadané sestavení musí mít silný název.<br /><br /> Sestavení, které vytvoříte pomocí parametru, `TemplateFile` bude satelitní sestavení. Tento parametr odpovídá `/template` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Timeout` | Volitelný `Int32` parametr.<br /><br /> Určuje dobu v milisekundách, po jejímž uplynutí je ukončen spustitelný soubor úlohy. Výchozí hodnota je `Int.MaxValue` , což značí, že není k dispozici žádný časový interval. |
| `Title` | Volitelný `String` parametr.<br /><br /> Určuje řetězec pro `Title` pole v sestavení. Další informace naleznete v dokumentaci k `/title` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ToolPath` | Volitelný `String` parametr.<br /><br /> Určuje umístění, ze kterého bude úloha načítat základní spustitelný soubor (Al.exe). Pokud tento parametr není zadán, úloha použije cestu instalace sady SDK odpovídající verzi rozhraní .NET Framework, která spouští nástroj MSBuild. |
| `Trademark` | Volitelný `String` parametr.<br /><br /> Určuje řetězec pro `Trademark` pole v sestavení. Další informace naleznete v dokumentaci k `/trade[mark]` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Version` | Volitelný `String` parametr.<br /><br /> Určuje informace o verzi pro toto sestavení. Formát řetězce je *hlavní_verze. podverze. sestavení. revize*. Výchozí hodnota je 0. Další informace naleznete v dokumentaci k `/v[ersion]` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Win32Icon` | Volitelný `String` parametr.<br /><br /> Vloží soubor *. ico* do sestavení. Soubor *. ico* poskytne výstupnímu souboru požadovaný vzhled v Průzkumníkovi souborů. Tento parametr odpovídá `/win32icon` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Win32Resource` | Volitelný `String` parametr.<br /><br /> Vloží prostředek systému Win32 (soubor *. res* ) do výstupního souboru. Další informace naleznete v dokumentaci k `/win32res` Možnosti v [Al.exe (linker sestavení)](/dotnet/framework/tools/al-exe-assembly-linker). |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

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

* [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
* [Úlohy](../msbuild/msbuild-tasks.md)
