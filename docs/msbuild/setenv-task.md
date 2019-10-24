---
title: Úloha setenv – | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ec3170c9662cd9ef67521addfdf0d0095bd23b3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747211"
---
# <a name="setenv-task"></a>Setenv – – úloha
Nastaví nebo odstraní hodnotu zadané proměnné prostředí.

## <a name="parameters"></a>Parametry
 Následující tabulka popisuje parametry úlohy **setenv –** .

|Parametr|Popis|
|---------------|-----------------|
|**Jméno**|Povinný parametr **řetězce**<br /><br /> Název proměnné prostředí.|
|**OutputEnvironmentVariable**|Volitelný výstupní parametr **řetězce** .<br /><br /> Obsahuje hodnotu, která je přiřazena proměnné prostředí, která je určena parametrem **Name** .|
|**Směr**|Povinný parametr `Boolean`.<br /><br /> Pokud `true`, zřetězí hodnotu parametru **Value** před hodnotu proměnné prostředí, která je určena parametrem **Name** , a poté přiřadí výsledek proměnné prostředí. Pokud `false`, přiřadí pouze hodnotu parametru **Value** proměnné prostředí.|
|**Cílové**|Volitelný **řetězcový** parametr.<br /><br /> Určuje umístění, kde je uložena proměnná prostředí. Zadejte "User" nebo "Machine".<br /><br /> Další informace najdete v tématu [výčet EnvironmentVariableTarget](xref:System.EnvironmentVariableTarget).|
|**Hodnota**|Volitelný **řetězcový** parametr.<br /><br /> Hodnota přiřazená proměnné prostředí, která je určena parametrem **Name** Pokud je **hodnota** prázdná a proměnná existuje, proměnná se odstraní. Pokud proměnná neexistuje, nedošlo k žádné chybě, i když operaci nelze provést.<br /><br /> Další informace naleznete v tématu [prostředí:: SetEnvironmentVariable metoda](xref:System.Environment.SetEnvironmentVariable%2A).|

## <a name="see-also"></a>Viz také:
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)