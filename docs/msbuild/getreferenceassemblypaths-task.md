---
title: Úloha GetReferenceAssemblyPaths – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56e3526f130a8717dec2dafeef794375ceffc37c
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579617"
---
# <a name="getreferenceassemblypaths-task"></a>GetReferenceAssemblyPaths – – úloha
Vrátí cesty referenčního sestavení různých rozhraní.

## <a name="parameters"></a>Parametry
 Následující tabulka popisuje parametry úlohy `GetReferenceAssemblyPaths`.

|Parametr|Popis|
|---------------|-----------------|
|`ReferenceAssemblyPaths`|Volitelný výstupní parametr `String[]`.<br /><br /> Vrátí cestu na základě parametru `TargetFrameworkMoniker`. Pokud je `TargetFrameworkMoniker` null nebo prázdné, bude tato cesta `String.Empty`.|
|`FullFrameworkReferenceAssemblyPaths`|Volitelný výstupní parametr `String[]`.<br /><br /> Vrátí cestu na základě parametru `TargetFrameworkMoniker` bez zvážení části profilu monikeru. Pokud je `TargetFrameworkMoniker` null nebo prázdné, bude tato cesta `String.Empty`.|
|`TargetFrameworkMoniker`|Volitelný parametr `String`.<br /><br /> Určuje moniker cílového rozhraní .NET Framework, který je přidružen k referenčním cestám sestavení.|
|`RootPath`|Volitelný parametr `String`.<br /><br /> Určuje kořenovou cestu, která se má použít k vygenerování cesty referenčního sestavení.|
|`BypassFrameworkInstallChecks`|Volitelný parametr <xref:System.Boolean>.<br /><br /> Pokud `true`, přeskočí základní kontroly, které `GetReferenceAssemblyPaths` ve výchozím nastavení provádí, aby bylo zajištěno, že jsou v závislosti na cílové architektuře nainstalovány konkrétní prostředí modulu runtime.|
|`TargetFrameworkMonikerDisplayName`|Volitelný výstupní parametr `String`.<br /><br /> Určuje zobrazovaný název pro moniker cílového rozhraní .NET Framework.|

## <a name="remarks"></a>Poznámky
 Kromě toho, že mají parametry, které jsou uvedeny v tabulce, tato úloha dědí parametry z třídy <xref:Microsoft.Build.Tasks.TaskExtension>, kterou sám dědí z třídy <xref:Microsoft.Build.Utilities.Task>. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)