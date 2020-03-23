---
title: FXC Úkol | Dokumenty společnosti Microsoft
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.fxc
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), FXC task
- FXC task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: 67958a1a1ebb2ff382d0896e2fbaec6105c0c785
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77279294"
---
# <a name="fxc-task"></a>Úkol FXC

V procesu sestavení použijte kompilátory shaderu HLSL.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry úlohy **FXC.**

|Parametr|Popis|
|---------------|-----------------|
|**Další includeředitelé adresáře**|Volitelný **parametr string[].**<br/><br/>Určuje jeden nebo více adresářů, které chcete přidat do cesty zahrnutí; oddělte středníky, pokud je více než jeden.<br/><br/>Použijte `/I[path]`.|
|**Další možnosti**|Volitelný parametr **řetězce.**|
|**AllResourcesBound**|Volitelný **parametr bool.**<br/><br/>Kompilátor bude předpokládat, že všechny prostředky, které shader může odkazovat jsou vázány a jsou v dobrém stavu po dobu provádění shaderu. K dispozici pro Shader Model 5.1 a vyšší.<br/><br/>Použijte `/all_resources_bound`.|
|**Výstup assembleru**|Volitelný parametr **řetězce.**<br/><br/>Určuje obsah výstupního souboru jazyka sestavení.<br/><br/>Použijte `/Fc, /Fx`.<br/><br/>**NoListing**<br/>**AssemblyCode**, `Fc`použijte .<br/>**AssemblyCodeAndHex**, `Fx`použijte .|
|**Soubor AssemblerOutputFile**|Volitelný parametr **řetězce.**<br/><br/>Určuje název souboru pro soubor výpisu kódu sestavení.|
|**CompileD2DCustomEffect**|Volitelný **parametr bool.**<br/><br/>Zkompilujte vlastní efekt Direct2D, který obsahuje shaderů obrazových bodů. Nepoužívejte pro vrchol nebo vypočítat vlastní efekt.|
|**ConsumeExportFile**|Volitelný parametr **řetězce.**|
|**Zakázat optimalizace**|Volitelný **parametr bool.**<br/><br/>Zakažte optimalizace.<br/><br/>`/Od`znamená, `/Gfp` že výstup nemusí `/Od /Gfp`být totožný s .|
|**Enable DebuggingInformation**|Volitelný **parametr bool.**<br/><br/>Povolte informace o ladění.|
|**EnableUnboundedDescriptorTables**|Volitelný **parametr bool.**<br/><br/>Informujte kompilátor, že shader může obsahovat deklaraci pole prostředků s neomezeným rozsahem. K dispozici pro Shader Model 5.1 a vyšší.<br/><br/>Použijte `/enable_unbounded_descriptor_tables`.|
|**Název EntryPointName**|Volitelný parametr **řetězce.**<br/><br/>Určuje název vstupního bodu pro shader.<br/><br/>Použijte `/E[name]`.|
|**GenerateExportFile**|Volitelný parametr **řetězce.**|
|**Generovat exportshaderprofil**|Volitelný parametr **řetězce.**|
|**Hlavičkový výstup**|Volitelný parametr **řetězce.**<br/><br/>Určuje název souboru záhlaví obsahujícího kód objektu.<br/><br/>Použijte `/Fh [name]`.|
|**Objekt ObjectFileOutput**|Volitelný parametr **řetězce.**<br/><br/>Určuje název souboru objektu.<br/><br/>Použijte `/Fo [name]`.|
|**Definice preprocesoru**|Volitelný **parametr string[].**<br/><br/>Definuje symboly předběžného zpracování pro zdrojový soubor.|
|**SetRootSignature**|Volitelný parametr **řetězce.**<br/><br/>Připojte kořenový podpis k bajtovému kódu shaderu. K dispozici pro Shader Model 5.0 a vyšší.<br/><br/>Použijte `/setrootsignature`.|
|**ShaderModel**|Volitelný parametr **řetězce.**<br/><br/>Určuje model shaderu. Některé typy shaderů lze použít pouze s nejnovějšími modely shaderu.<br/><br/>Použijte `/T [type]_[model]`.|
|**Typ shaderu**|Volitelný parametr **řetězce.**<br/><br/>Určuje typ shaderu.<br/><br/>Použijte `/T [type]_[model]`.<br/><br/>**Efekt**, `fx`použijte .<br/>**Vrchol**, `vs`použijte .<br/>**Pixel**, `ps`použijte .<br/>**Geometrie** `gs`, použití .<br/>**Trup**, `hs`použijte .<br/>**Doména** `ds`, použijte .<br/>**Vypočítat** `cs`, použijte .<br/>**Knihovna** `lib`, použijte .<br/>**RootSignature**, generovat kořenový podpisový objekt.|
|**Zdroj**|Povinný parametr **ITaskItem.**|
|**PotlačitStartupBanner**|Volitelný **parametr bool.**<br/><br/>Potlačí zobrazení spouštěcího banneru a informační zprávy.<br/><br/>Použijte `/nologo`.|
|**TrackerLogDirectory**|Volitelný parametr **řetězce.**|
|**TreatWarningAsChyba**|Volitelný **parametr bool.**<br/><br/>Považuje všechna upozornění kompilátoru za chyby.<br/><br/>Pro nový projekt může být nejlepší `/WX` použít ve všech kompilacích; vyřešení všech varování zajistí co nejméně chyb kódu, které se dá těžko najít.|
|**NázevProměnné**|Volitelný parametr **řetězce.**<br/><br/>Určuje název názvu proměnné v souboru záhlaví.<br/><br/>Použijte `/Vn [name]`.|

## <a name="see-also"></a>Viz také

[Odkaz na úkol](../msbuild/msbuild-task-reference.md)