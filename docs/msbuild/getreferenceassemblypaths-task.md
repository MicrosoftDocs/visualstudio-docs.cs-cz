---
title: Úloha GetReferenceAssemblyPaths | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: d2ca532e37fa2f70800416539a7de2ff5e9978e2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633977"
---
# <a name="getreferenceassemblypaths-task"></a>Úloha GetReferenceAssemblyPaths

Vrátí cesty referenčního sestavení různých rámců.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `GetReferenceAssemblyPaths` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`ReferenceAssemblyPaths`|Volitelný `String[]` výstupní parametr.<br /><br /> Vrátí cestu na základě `TargetFrameworkMoniker` parametru. Pokud `TargetFrameworkMoniker` je null nebo prázdný, `String.Empty`bude tato cesta .|
|`FullFrameworkReferenceAssemblyPaths`|Volitelný `String[]` výstupní parametr.<br /><br /> Vrátí cestu na základě `TargetFrameworkMoniker` parametru bez ohledu na profilovou část zástupného názvového názvového názvového názvového názvového protokolu. Pokud `TargetFrameworkMoniker` je null nebo prázdný, `String.Empty`bude tato cesta .|
|`TargetFrameworkMoniker`|Volitelný `String` parametr.<br /><br /> Určuje zástupný název cílového rámce, který je přidružen k cestám sestavy odkazu.|
|`RootPath`|Volitelný `String` parametr.<br /><br /> Určuje kořenovou cestu, která má být používána ke generování cesty sestavy odkazu.|
|`BypassFrameworkInstallChecks`|Volitelný <xref:System.Boolean> parametr.<br /><br /> Pokud `true`, obchází `GetReferenceAssemblyPaths` základní kontroly, které provádí ve výchozím nastavení zajistit, že jsou nainstalovány určité rozhraní runtime, v závislosti na cílové rozhraní.|
|`TargetFrameworkMonikerDisplayName`|Volitelný `String` výstupní parametr.<br /><br /> Určuje zobrazovaný název zástupového názvu cílové architektury.|

## <a name="remarks"></a>Poznámky

 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha <xref:Microsoft.Build.Tasks.TaskExtension> dědí parametry z <xref:Microsoft.Build.Utilities.Task> třídy, která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)