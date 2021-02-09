---
title: Úloha UpdateManifest – | Microsoft Docs
description: Přečtěte si, jak MSBuild používá úlohu UpdateManifest – k aktualizaci vybraných vlastností v manifestu a opětovném podepsání.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UpdateManifest task
- UpdateManifest task [MSBuild]
ms.assetid: 1291fd33-b89e-4e15-8fb1-69f9625cf2d2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b8bb090b66a52e9c2931e8bf4afc878d87a0ae36
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902496"
---
# <a name="updatemanifest-task"></a>UpdateManifest – úloha

Aktualizuje vybrané vlastnosti v manifestu a znovu se podepíše.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `UpdateManifest` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`ApplicationManifest`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje manifest aplikace.|
|`ApplicationPath`|Požadovaný parametr `String`.<br /><br /> Určuje cestu k manifestu aplikace.|
|`InputManifest`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje manifest, který se má aktualizovat.|
|`OutputManifest`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> výstupní parametr.<br /><br /> Určuje manifest, který obsahuje aktualizované vlastnosti.|

## <a name="remarks"></a>Poznámky

 Kromě parametrů uvedených v tabulce zdědí tento úkol parametry z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisů naleznete v tématu [základní třída Task](../msbuild/task-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)