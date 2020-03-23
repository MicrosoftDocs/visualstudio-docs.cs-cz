---
title: Označit | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4bf89469c4137052247b5a1fdfee7f8dc694fbcc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773991"
---
# <a name="mark"></a>Označení
Volba *VSPerfCmd.exe* **Mark** vloží zadané informace do datového souboru profilování. Označit může být uvedenv samostatné sestavě VSPerfReport nebo v zobrazení sestavy značek v umělosti profileru. **Značku** lze použít k určení počátečních a koncových bodů ve filtrech sestavy a zobrazení.

 Možnost **Označit** musí být jedinou možností určenou na příkazovém řádku.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Mark:MarkID,[MarkName]
```

#### <a name="parameters"></a>Parametry
 `MarkID`Celé číslo definované uživatelem, které je uvedeno jako ID značky v zobrazeních profileru a sestavách. `MarkID`nemusí být jedinečný.

 `MarkName`(Nepovinné) Uživatelem definovaný řetězec, který je uveden jako Označit název v zobrazeních profileru a sestavách. Pokud `MarkName` není zadán, je pole Označit název seznamu značek prázdné. Řetězce, které obsahují mezery nebo lomítka ("/") uzavřete do uvozovek.

## <a name="example"></a>Příklad
 Tento příklad vloží značku s ID 123 a název značky "TestMark".

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
VSPerfCmd.exe /Mark:123,TestMark
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
