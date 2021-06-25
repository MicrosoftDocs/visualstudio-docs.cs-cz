---
title: Správce ladění relací | Microsoft Docs
description: Seznamte se se správcem ladění relací, který spravuje více ladicích modulů a ladí programy ve více procesech napříč libovolným počtem počítačů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 217a2d401e61c58a58d958bb754265a19a2a367d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902082"
---
# <a name="session-debug-manager"></a>Správce ladění relací
Správce ladění relací (SDM) spravuje libovolný počet ladicích modulů (DE), které ladí libovolný počet programů ve více procesech napříč libovolným počtem počítačů. Kromě multiplexeru ladicího stroje poskytuje SDM jednotné zobrazení ladicí relace k integrovanému vývojovému prostředí( IDE).

## <a name="session-debug-manager-operation"></a>Operace správce ladění relace
 DE spravuje správce ladění relací (SDM). Současně může na počítači běžet více než jeden ladicí modul. Pro multiplexování prostředí IDE zabalí SDM několik rozhraní z prostředí IDE a zpřístupní je v integrovaném vývojovém prostředí jako jedno rozhraní.

 Pro zvýšení výkonu nejsou některá rozhraní multiplexní. Místo toho se používají přímo z DE a volání těchto rozhraní prochádí přes SDM. Například rozhraní používaná s kontexty paměti, kódu a dokumentu nejsou multiplexní, protože odkazují na konkrétní instrukci, paměť nebo dokument v určitém programu laděném konkrétním de. Na této úrovni komunikace není potřeba zapojit žádné jiné destrukce.

 To není pravdivé pro všechny kontexty. Volání rozhraní kontextu vyhodnocení výrazu prochádí přes SDM. Během vyhodnocování výrazu SDM zabalí rozhraní [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) které poskytuje integrovanému vývojovému prostředí, protože při vyhodnocení tohoto výrazu může zahrnovat více edcí, které ladí programy ve stejném procesu, který může být spuštěn ve stejném vlákně.

 SDM obvykle funguje jako mechanismus delegování, ale může fungovat jako mechanismus všesměrového vysílání. Například během vyhodnocování výrazu funguje SDM jako mechanismus všesměrového vysílání, který upozorní všechny objekty DE, že mohou spouštět kód v zadaném vlákně. Podobně když SDM obdrží událost zastavení, všesměrově vysílá do programů, které by měly přestat běžet. Když se volá krok, SDM všesměrově vysílá programům, které mohou pokračovat v provozu. Zarážky se také vysílá do každého DE.

 SDM nesleduje aktuální program, vlákno nebo rámec zásobníku. Informace o procesu, programu a vláknu se posílají do SDM ve spojení s konkrétními událostmi ladění.

## <a name="see-also"></a>Viz také
- [Ladicí modul](../../extensibility/debugger/debug-engine.md)
- [Komponenty ladicího programu](../../extensibility/debugger/debugger-components.md)
- [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md)
