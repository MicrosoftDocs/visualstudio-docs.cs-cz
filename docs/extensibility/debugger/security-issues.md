---
title: Bezpečnostní otázky | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40898f5633eac374206ed40bfcac96d9c1c5b753
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713051"
---
# <a name="security-issues"></a>Problémy se zabezpečením
Chcete-li ladit program pomocí sady Visual Studio, jsou potřeba pouze oprávnění, která vývojář potřebuje ke spuštění programu. To zahrnuje vzdálené ladění pro většinu situací. Některé situace, které zahrnují jiné služby, například Internetovou informační službu, mohou vyžadovat vyšší úroveň oprávnění.

 Při spuštění sady Visual Studio sleduje správce ladění procesů (PDM) procesy ladění v místním počítači. Vzdáleně je vývojářem spuštěn program s názvem *msvsmon.exe,* který zpracovává vzdálené ladění a zpřístupňování pdm. (*msvsmon.exe* není služba a musí být spuštěna ručně povolit vzdálené ladění v tomto počítači.) Pokud visual studio (nebo *msvsmon.exe*) není spuštěna, žádné procesy jsou sledovány pro ladění.

 Vývojář může ladit programy, které začaly, bez zvláštních oprávnění. Vývojář může dokonce ladit procesy spuštěné jiným uživatelem, pokud je tato jiná osoba členem stejné skupiny zabezpečení. A chcete-li povolit vzdálené ladění, je nutné pouze zkopírovat požadované soubory do vzdáleného počítače a spustit *msvsmon.exe*. Další informace naleznete [v tématu Vzdálené ladění](../../debugger/remote-debugging.md).

## <a name="see-also"></a>Viz také
- [Ladění úkolů](../../extensibility/debugger/debugging-tasks.md)
- [Správce ladění procesu](../../extensibility/debugger/process-debug-manager.md)
- [Vzdálené ladění](../../debugger/remote-debugging.md)
