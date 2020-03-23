---
title: Úkol SetEnv | Dokumenty společnosti Microsoft
ms.date: 11/05/2018
ms.topic: reference
f1_keywords:
- vc.task.setenv
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), tasks
- SetEnv task (MSBuild (C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5df538e7eb86a20dfc06e6e6558bded577ba3d2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632378"
---
# <a name="setenv-task"></a>Úloha SetEnv

Nastaví nebo odstraní hodnotu zadané proměnné prostředí.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy **SetEnv.**

|Parametr|Popis|
|---------------|-----------------|
|**Název**|Povinný **parametr String.**<br /><br /> Název proměnné prostředí.|
|**Proměnná výstupního prostředí**|Volitelný výstupní parametr **String.**<br /><br /> Obsahuje hodnotu, která je přiřazena proměnné prostředí, která je určena **name** parametr.|
|**Předpona**|Povinný `Boolean` parametr.<br /><br /> Pokud `true`zřetězí hodnotu parametru **Value** před hodnotou proměnné prostředí, která je určena parametrem **Name,** a pak přiřadí výsledek proměnné prostředí. If `false`, přiřadí pouze hodnotu parametru **Value** proměnné prostředí.|
|**Cíl**|Volitelný **parametr String.**<br /><br /> Určuje umístění, kde je uložena proměnná prostředí. Zadejte "Uživatel" nebo "Stroj".<br /><br /> Další informace naleznete v tématu [EnvironmentVariableTarget Výčet](xref:System.EnvironmentVariableTarget).|
|**Hodnotu**|Volitelný **parametr String.**<br /><br /> Hodnota přiřazená proměnné prostředí, která je určena parametrem **Name.** Pokud **Value** je prázdný a proměnná existuje, proměnná je odstraněn. Pokud proměnná neexistuje, dojde k žádné chybě i v případě, že operaci nelze provést.<br /><br /> Další informace naleznete v [tématu Environment::SetEnvironmentVariable Method](xref:System.Environment.SetEnvironmentVariable%2A).|

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
