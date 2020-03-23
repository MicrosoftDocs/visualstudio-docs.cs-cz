---
title: Úloha ResolveKeySource | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 3aa4e2454a0216e697ed12404091eb0ef16416cb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632703"
---
# <a name="resolvekeysource-task"></a>ResolveKeySource – úloha

Určuje zdroj klíče silného názvu.

## <a name="task-parameters"></a>Parametry úlohy

 Následující tabulka popisuje parametry `ResolveKeySource` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`AutoClosePasswordPromptShow`|Volitelný `Int32` parametr.<br /><br /> Získá nebo nastaví množství času v sekundách, chcete-li zobrazit zprávu odpočítávání.|
|`AutoClosePasswordPromptTimeout`|Volitelný `Int32` parametr.<br /><br /> Získá nebo nastaví dobu v sekundách, než zavřete dialogové okno s výzvou k zadání hesla.|
|`CertificateFile`|Volitelný `String` parametr.<br /><br /> Získá nebo nastaví cestu k souboru certifikátu.|
|`CertificateThumbprint`|Volitelný `String` parametr.<br /><br /> Získá nebo nastaví kryptografický otisk certifikátu.|
|`KeyFile`|Volitelný `String` parametr.<br /><br /> Získá nebo nastaví cestu k souboru klíče.|
|`ResolvedKeyContainer`|Volitelný `String` výstupní parametr.<br /><br /> Získá nebo nastaví kontejner vyřešený klíč.|
|`ResolvedKeyFile`|Volitelný `String` výstupní parametr.<br /><br /> Získá nebo nastaví soubor vyřešeného klíče.|
|`ResolvedThumbprint`|Volitelný `String` výstupní parametr.<br /><br /> Získá nebo nastaví kryptografický otisk vyřešeného certifikátu.|
|`ShowImportDialogDespitePreviousFailures`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`zobrazíte dialogové okno importu i přes předchozí selhání.|
|`SuppressAutoClosePasswordPrompt`|Volitelný `Boolean` parametr.<br /><br /> Získá nebo nastaví logickou hodnotu, která určuje, zda dialogové okno s výzvou k zadání hesla nemá automaticky zavřít.|

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
