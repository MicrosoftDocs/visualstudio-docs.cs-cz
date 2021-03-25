---
title: Problémy se zabezpečením | Microsoft Docs
description: Přečtěte si o oprávněních potřebných k ladění programu pomocí sady Visual Studio, včetně vzdáleného ladění a situací, které zahrnují další služby.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1994a4a95d005edf4a71df3a1bb899522ecec137
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070424"
---
# <a name="security-issues"></a>Problémy se zabezpečením
Chcete-li ladit program pomocí sady Visual Studio, jsou jediná potřebná oprávnění stejná jako vývojář, který vyžaduje spuštění programu. To zahrnuje vzdálené ladění ve většině situací. V některých situacích, které se týkají jiných služeb, jako je třeba Internetová informační služba, může vyžadovat vyšší úroveň oprávnění.

 I když je spuštěná aplikace Visual Studio, sleduje správce ladění procesů (PDM) procesy ladění na místním počítači. Vzdáleně je program s názvem *msvsmon.exe* spuštěn vývojářem, který zpracovává vzdálené ladění a zpřístupňuje PDM. (*msvsmon.exe* není služba a je nutné ji spustit ručně, aby se na tomto počítači povolilo vzdálené ladění.) Pokud není spuštěna aplikace Visual Studio (nebo *msvsmon.exe*), nejsou sledovány žádné procesy pro ladění.

 Vývojář může ladit programy, které zahájily bez zvláštních oprávnění. Vývojář může dokonce ladit procesy zahájené někým jiným, pokud je tato jiná osoba členem stejné skupiny zabezpečení. Aby bylo možné povolit vzdálené ladění, je nutné pouze zkopírovat požadované soubory do vzdáleného počítače a spustit *msvsmon.exe*. Další informace najdete v tématu [vzdálené ladění](../../debugger/remote-debugging.md).

## <a name="see-also"></a>Viz také
- [Úlohy ladění](../../extensibility/debugger/debugging-tasks.md)
- [Správce ladění procesů](../../extensibility/debugger/process-debug-manager.md)
- [Vzdálené ladění](../../debugger/remote-debugging.md)
