---
title: Úloha GetReferenceAssemblyPaths – | Microsoft Docs
description: Použijte úlohu MSBuild GetReferenceAssemblyPaths – k vrácení referenčních cest sestavení různých rozhraní.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d3e0afdc7486e4337a92e3639c23c404050a84c4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914605"
---
# <a name="getreferenceassemblypaths-task"></a>GetReferenceAssemblyPaths – úloha

Vrátí cesty referenčního sestavení různých rozhraní.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `GetReferenceAssemblyPaths` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`ReferenceAssemblyPaths`|Volitelný `String[]` výstupní parametr.<br /><br /> Vrátí cestu na základě `TargetFrameworkMoniker` parametru. Pokud má `TargetFrameworkMoniker` hodnotu null nebo je prázdná, bude tato cesta `String.Empty` .|
|`FullFrameworkReferenceAssemblyPaths`|Volitelný `String[]` výstupní parametr.<br /><br /> Vrátí cestu na základě `TargetFrameworkMoniker` parametru bez zvážení části profilu monikeru. Pokud má `TargetFrameworkMoniker` hodnotu null nebo je prázdná, bude tato cesta `String.Empty` .|
|`TargetFrameworkMoniker`|Volitelný `String` parametr.<br /><br /> Určuje moniker cílového rozhraní .NET Framework, který je přidružen k referenčním cestám sestavení.|
|`RootPath`|Volitelný `String` parametr.<br /><br /> Určuje kořenovou cestu, která se má použít k vygenerování cesty referenčního sestavení.|
|`BypassFrameworkInstallChecks`|Volitelný <xref:System.Boolean> parametr.<br /><br /> Pokud `true` , obchází základní kontroly, které `GetReferenceAssemblyPaths` jsou ve výchozím nastavení prováděny, aby bylo zajištěno, že jsou v závislosti na cílové architektuře nainstalovány konkrétní prostředí modulu runtime.|
|`TargetFrameworkMonikerDisplayName`|Volitelný `String` výstupní parametr.<br /><br /> Určuje zobrazovaný název pro moniker cílového rozhraní .NET Framework.|

## <a name="remarks"></a>Poznámky

 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)