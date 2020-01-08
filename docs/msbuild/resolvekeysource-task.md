---
title: Úloha ResolveKeySource – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveKeySource task [MSBuild]
- MSBuild, ResolveKeySource task
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 09b3917e1c67014a780d11e2ae9a944844e63e25
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595186"
---
# <a name="resolvekeysource-task"></a>ResolveKeySource – úloha
Určuje zdroj klíče se silným názvem.

## <a name="task-parameters"></a>Parametry úlohy
 Následující tabulka popisuje parametry úlohy `ResolveKeySource`.

|Parametr|Popis|
|---------------|-----------------|
|`AutoClosePasswordPromptShow`|Volitelný parametr `Int32`.<br /><br /> Získá nebo nastaví množství času (v sekundách), ve kterém se má zobrazit zpráva o počtu.|
|`AutoClosePasswordPromptTimeout`|Volitelný parametr `Int32`.<br /><br /> Získá nebo nastaví množství času (v sekundách), po který se má čekat před zavřením dialogového okna výzvy k zadání hesla.|
|`CertificateFile`|Volitelný parametr `String`.<br /><br /> Získá nebo nastaví cestu k souboru certifikátu.|
|`CertificateThumbprint`|Volitelný parametr `String`.<br /><br /> Získá nebo nastaví kryptografický otisk certifikátu.|
|`KeyFile`|Volitelný parametr `String`.<br /><br /> Získá nebo nastaví cestu k souboru klíče.|
|`ResolvedKeyContainer`|Volitelný výstupní parametr `String`.<br /><br /> Získá nebo nastaví vyřešený kontejner klíčů.|
|`ResolvedKeyFile`|Volitelný výstupní parametr `String`.<br /><br /> Získá nebo nastaví přeložený soubor klíče.|
|`ResolvedThumbprint`|Volitelný výstupní parametr `String`.<br /><br /> Získá nebo nastaví přeložený kryptografický otisk certifikátu.|
|`ShowImportDialogDespitePreviousFailures`|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, Zobrazit dialog pro import navzdory předchozím chybám|
|`SuppressAutoClosePasswordPrompt`|Volitelný parametr `Boolean`.<br /><br /> Získá nebo nastaví logickou hodnotu, která určuje, zda se má dialogové okno výzvy k zadání hesla automaticky zavřít.|

## <a name="remarks"></a>Poznámky
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také:
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
