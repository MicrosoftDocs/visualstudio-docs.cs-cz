---
title: Označit | Microsoft Docs
description: Přečtěte si, jak VSPerfCmd.exe možnost označení vloží zadané informace do souboru dat profilování.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 33a343be010a5bf9cc0d9ba3e4251d92fd720656
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917815"
---
# <a name="mark"></a>Označení
Možnost *VSPerfCmd.exe* **značka** vloží zadané informace do souboru dat profilování. Značka může být uvedena v samostatné sestavě VSPerfReport nebo v zobrazení zprávy pro uživatelské rozhraní profileru. **Značku** lze použít k určení počátečních a koncových bodů v filtrech sestav a zobrazení.

 Možnost **Mark** musí být jedinou možností zadanou v příkazovém řádku.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Mark:MarkID,[MarkName]
```

#### <a name="parameters"></a>Parametry
 `MarkID` Uživatelsky definované celé číslo, které je uvedeno jako ID značky v zobrazeních a sestavách profileru. `MarkID` nemusí být jedinečný.

 `MarkName` Volitelné Uživatelem definovaný řetězec, který je uveden jako název značky v zobrazeních a sestavách profileru. Není `MarkName` -li parametr zadán, je pole název značky v seznamu značek prázdné. Uzavřete řetězce, které obsahují mezery nebo lomítka ("/") v uvozovkách.

## <a name="example"></a>Příklad
 Tento příklad vloží značku s ID 123 a názvem "TestMark".

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
VSPerfCmd.exe /Mark:123,TestMark
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
