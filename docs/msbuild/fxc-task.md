---
title: Úloha FXC | Microsoft Docs
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
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 766a3dc35d72e21fc0aca9436ebff25dc3193a2e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747328"
---
# <a name="fxc-task"></a>FXC – úloha

Použijte kompilátory HLSL shaderu v procesu sestavení.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry úlohy **fxc** .

|Parametr|Popis|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|Parametr volitelného **řetězce []** .<br/><br/>Určuje jeden nebo více adresářů, které mají být přidány do cesty include; oddělte je středníkem, pokud je více než jedna.<br/><br/>Použijte `/I[path]`.|
|**AdditionalOptions**|Volitelný **řetězcový** parametr.|
|**AllResourcesBound**|Volitelný parametr **bool** .<br/><br/>Kompilátor předpokládá, že všechny prostředky, na které může shader odkazovat, jsou svázané a jsou v dobrém stavu po dobu trvání běhu shaderu. K dispozici pro shader model 5,1 a vyšší.<br/><br/>Použijte `/all_resources_bound`.|
|**AssemblerOutput**|Volitelný **řetězcový** parametr.<br/><br/>Určuje obsah výstupního souboru jazyka sestavení.<br/><br/>Použijte `/Fc, /Fx`.<br/><br/>**Seznam není**<br/>**AssemblyCode**použijte `Fc`.<br/>**AssemblyCodeAndHex**použijte `Fx`.|
|**AssemblerOutputFile**|Volitelný **řetězcový** parametr.<br/><br/>Určuje název souboru výpisu kódu sestavení.|
|**CompileD2DCustomEffect**|Volitelný parametr **bool** .<br/><br/>Zkompilujte vlastní efekt Direct2D, který obsahuje pixel shadery. Nepoužívejte pro svůj vlastní efekt vrcholů nebo výpočtů.|
|**ConsumeExportFile**|Volitelný **řetězcový** parametr.|
|**DisableOptimizations**|Volitelný parametr **bool** .<br/><br/>Zakáže optimalizace.<br/><br/>`/Od` implikuje `/Gfp`, i když výstup nemusí být stejný jako `/Od /Gfp`.|
|**EnableDebuggingInformation**|Volitelný parametr **bool** .<br/><br/>Povolit ladicí informace.|
|**EnableUnboundedDescriptorTables**|Volitelný parametr **bool** .<br/><br/>Informujte kompilátor, že shader může obsahovat deklaraci pole prostředků s neohraničeným rozsahem. K dispozici pro shader model 5,1 a vyšší.<br/><br/>Použijte `/enable_unbounded_descriptor_tables`.|
|**Parametr EntryPoint**|Volitelný **řetězcový** parametr.<br/><br/>Určuje název vstupního bodu pro shader.<br/><br/>Použijte `/E[name]`.|
|**GenerateExportFile**|Volitelný **řetězcový** parametr.|
|**GenerateExportShaderProfile**|Volitelný **řetězcový** parametr.|
|**HeaderFileOutput**|Volitelný **řetězcový** parametr.<br/><br/>Určuje název hlavičkového souboru obsahujícího kód objektu.<br/><br/>Použijte `/Fh [name]`.|
|**ObjectFileOutput**|Volitelný **řetězcový** parametr.<br/><br/>Určuje název souboru objektu.<br/><br/>Použijte `/Fo [name]`.|
|**PreprocessorDefinitions**|Parametr volitelného **řetězce []** .<br/><br/>Definuje symboly předzpracování pro zdrojový soubor.|
|**SetRootSignature**|Volitelný **řetězcový** parametr.<br/><br/>Připojte kořenový podpis k bytovému kódu shaderu. K dispozici pro shader model 5,0 a vyšší.<br/><br/>Použijte `/setrootsignature`.|
|**ShaderModel**|Volitelný **řetězcový** parametr.<br/><br/>Určuje model shaderu. Některé typy shaderů lze použít pouze s nejnovějšími modely shaderů.<br/><br/>Použijte `/T [type]_[model]`.|
|**ShaderType**|Volitelný **řetězcový** parametr.<br/><br/>Určuje typ shaderu.<br/><br/>Použijte `/T [type]_[model]`.<br/><br/>**Efekt**použijte `fx`.<br/>**Vrchol**použijte `vs`.<br/>**Pixel**, použijte `ps`.<br/>**Geometrie**, použijte `gs`.<br/>**Trup**použijte `hs`.<br/>**Doména**, použijte `ds`.<br/>**COMPUTE**, použijte `cs`.<br/>**Knihovny**, použijte `lib`.<br/>**RootSignature**, vygenerujte objekt kořenového podpisu.|
|**Zdrojová**|Povinný parametr **ITaskItem**|
|**SuppressStartupBanner**|Volitelný parametr **bool** .<br/><br/>Potlačí zobrazení úvodního nápisu a informační zprávy.<br/><br/>Použijte `/nologo`.|
|**TrackerLogDirectory**|Volitelný **řetězcový** parametr.|
|**TreatWarningAsError**|Volitelný parametr **bool** .<br/><br/>Zpracovává všechna upozornění kompilátoru jako chyby.<br/><br/>Pro nový projekt může být nejvhodnější použít `/WX` ve všech kompilacích; řešení všech upozornění zajistí nejmenší možné nedostatky v obtížném hledání kódu.|
|**VariableName**|Volitelný **řetězcový** parametr.<br/><br/>Určuje název proměnné v hlavičkovém souboru.<br/><br/>Použijte `/Vn [name]`.|

## <a name="see-also"></a>Viz také:

[Odkaz na úkol](../msbuild/msbuild-task-reference.md)