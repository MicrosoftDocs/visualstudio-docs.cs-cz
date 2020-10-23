---
title: Úloha GenerateTrustInfo – | Microsoft Docs
description: Použijte úlohu MSBuild GenerateTrustInfo – k vygenerování vztahu důvěryhodnosti aplikace ze základního manifestu a parametrů TargetZone a ExcludedPermissions.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8a90188244e32b6f593affd2c29a227a2810227d
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436448"
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo – úloha

Generuje vztah důvěryhodnosti aplikace ze základního manifestu a z `TargetZone` `ExcludedPermissions` parametrů a.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `GenerateTrustInfo` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`ApplicationDependencies`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje závislá sestavení.|
|`BaseManifest`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje základní manifest, ze kterého se má vygenerovat vztah důvěryhodnosti aplikace.|
|`ExcludedPermissions`|Volitelný `String` parametr.<br /><br /> Určuje jednu nebo víc hodnot identity oprávnění oddělených středníkem, které se mají vyloučit ze sady výchozích oprávnění zóny.|
|`TargetZone`|Volitelný `String` parametr.<br /><br /> Určuje výchozí sadu oprávnění zóny, která se získá ze zásad počítače.|
|`TrustInfoFile`|Vyžaduje se <xref:Microsoft.Build.Framework.ITaskItem> výstupní parametr.<br /><br /> Určuje soubor, který obsahuje informace o vztahu důvěryhodnosti zabezpečení aplikace.|

## <a name="remarks"></a>Poznámky

 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)