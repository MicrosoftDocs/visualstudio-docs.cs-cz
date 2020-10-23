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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e38a0f1aea6999e30d2ab2493873f66cd907878
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436891"
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