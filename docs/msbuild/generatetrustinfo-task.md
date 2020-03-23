---
title: Úloha GenerateTrustInfo | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateTrustInfo task
- GenerateTrustInfo task [MSBuild]
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e84007c9a10618c6d757a36debe58c272302fa3e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634029"
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo – úloha

Generuje vztah důvěryhodnosti aplikace ze základního `TargetZone` `ExcludedPermissions` manifestu a z parametrů a.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `GenerateTrustInfo` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`ApplicationDependencies`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje závislá sestavení.|
|`BaseManifest`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje základní manifest, ze který má být generován vztah důvěryhodnosti aplikace.|
|`ExcludedPermissions`|Volitelný `String` parametr.<br /><br /> Určuje jednu nebo více hodnot identity oprávnění oddělených středníkem, které mají být vyloučeny z výchozí sady oprávnění zóny.|
|`TargetZone`|Volitelný `String` parametr.<br /><br /> Určuje výchozí sadu oprávnění zóny, která je získána ze zásad počítače.|
|`TrustInfoFile`|Požadovaný <xref:Microsoft.Build.Framework.ITaskItem> výstupní parametr.<br /><br /> Určuje soubor, který obsahuje informace o důvěryhodnosti zabezpečení aplikace.|

## <a name="remarks"></a>Poznámky

 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha <xref:Microsoft.Build.Tasks.TaskExtension> dědí parametry z <xref:Microsoft.Build.Utilities.Task> třídy, která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)