---
title: Úloha FormatUrl – | Microsoft Docs
description: Přečtěte si, jak pomocí úlohy MSBuild FormatUrl – převést vstupní adresu URL na správný formát výstupní adresy URL.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FormatUrl task
- FormatUrl task [MSBuild]
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a9a05ce16289c012b067faa5bc302a3921cbe1c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888092"
---
# <a name="formaturl-task"></a>FormatUrl – úloha

Převede adresu URL na správný formát adresy URL.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `FormatUrl` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`InputUrl`|Volitelný `String` parametr.<br /><br /> Určuje adresu URL, která má být naformátovaná.|
|`OutputUrl`|Volitelný `String` výstupní parametr.<br /><br /> Určuje formátovanou adresu URL.|

## <a name="remarks"></a>Poznámky

 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)