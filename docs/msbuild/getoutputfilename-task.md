---
title: Úloha GetOutputFileName | Microsoft Docs
description: Použijte úlohu pomocníka MSBuild GetOutputFileName k určení možností pro název výstupního souboru pro cl.exe a další nástroje.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutputfilename
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), GetOutputFileName task
- GetOutputFileName task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: cb4670bb84b151332951608f7b20ef5ea44e59a3
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436781"
---
# <a name="getoutputfilename-task"></a>GetOutputFileName – úloha

Pomocná úloha pro získání názvu výstupního souboru CL a dalších nástrojů, které umožňují zadat jenom výstupní adresář nebo úplný název souboru nebo nic.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry úlohy **GetOutputFileName** .

|Parametr|Popis|
|---------------|-----------------|
|**OutputExtension**|Povinný parametr **řetězce**|
|**OutputFile**|Volitelný výstupní parametr **řetězce** .|
|**OutputPath**|Volitelný **řetězcový** parametr.|
|**Požadovaný sourcefile**|Povinný parametr **řetězce**|

## <a name="see-also"></a>Viz také

[Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
