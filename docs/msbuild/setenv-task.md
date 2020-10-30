---
title: Úloha setenv – | Microsoft Docs
description: Přečtěte si, jak MSBuild používá úlohu setenv – k nastavení nebo odstranění hodnoty zadané proměnné prostředí.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f7267e90c2fe3e4617fe2bec8bb177baf42ce37b
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048314"
---
# <a name="setenv-task"></a>SetEnv – úloha

Nastaví nebo odstraní hodnotu zadané proměnné prostředí.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy **setenv –** .

|Parametr|Popis|
|---------------|-----------------|
|**Název**|Povinný parametr **řetězce**<br /><br /> Název proměnné prostředí.|
|**OutputEnvironmentVariable**|Volitelný výstupní parametr **řetězce** .<br /><br /> Obsahuje hodnotu, která je přiřazena proměnné prostředí, která je určena parametrem **Name** .|
|**Předpona**|Povinný `Boolean` parametr.<br /><br /> Pokud `true` , zřetězí hodnotu parametru **Value** před hodnotu proměnné prostředí, která je určena parametrem **Name** , a poté přiřadí výsledek proměnné prostředí. Pokud `false` , přiřadí pouze hodnotu parametru **Value** proměnné prostředí.|
|**Cílové**|Volitelný **řetězcový** parametr.<br /><br /> Určuje umístění, kde je uložena proměnná prostředí. Zadejte "User" nebo "Machine".<br /><br /> Další informace najdete v tématu [výčet EnvironmentVariableTarget](xref:System.EnvironmentVariableTarget).|
|**Hodnota**|Volitelný **řetězcový** parametr.<br /><br /> Hodnota přiřazená proměnné prostředí, která je určena parametrem **Name** Pokud je **hodnota** prázdná a proměnná existuje, proměnná se odstraní. Pokud proměnná neexistuje, nedošlo k žádné chybě, i když operaci nelze provést.<br /><br /> Další informace naleznete v tématu [prostředí:: SetEnvironmentVariable metoda](xref:System.Environment.SetEnvironmentVariable%2A).|

## <a name="see-also"></a>Viz také

- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
