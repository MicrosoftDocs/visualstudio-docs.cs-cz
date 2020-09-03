---
title: Správce ladění relace | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 953b4e948ef5e21531a3e73bceed3a363ed3cec5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712875"
---
# <a name="session-debug-manager"></a>Správce ladění relace
Správce ladění relace (SDM) spravuje libovolný počet ladicích modulů (DE), které ladí libovolný počet programů ve více procesech napříč libovolným počtem počítačů. Kromě toho, že se jedná o multiplexor ladicího stroje, model SDM poskytuje jednotný přehled o relaci ladění IDE.

## <a name="session-debug-manager-operation"></a>Operace Správce ladění relace
 Správce ladění relace (SDM) spravuje DE. V počítači může být spuštěno více než jeden ladicí modul současně. Pro multiplexování algoritmu DEs zalomí model SDM mnoho rozhraní z algoritmu DEs a zpřístupňuje je rozhraní IDE jako jediné rozhraní.

 Aby se zvýšil výkon, některá rozhraní se nemultiplexují. Místo toho se používají přímo z DE a volání do těchto rozhraní neprojde přes SDM. Například rozhraní používaná s kontexty paměti, kódu a dokumentu nejsou multiplexovaná, protože odkazují na konkrétní instrukci, paměť nebo dokument v určitém programu, který ladit konkrétní DE. V této úrovni komunikace není potřeba žádný jiný DE.

 To není pravdivé u všech kontextů. Volání rozhraní kontextu vyhodnocení výrazu procházejí přes SDM. Během vyhodnocování výrazu model SDM zabalí rozhraní [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , které poskytuje rozhraní IDE, protože při vyhodnocování tohoto výrazu může zahrnovat několik des, které ladí programy ve stejném procesu, který může být spuštěn ve stejném vlákně.

 SDM obvykle funguje jako mechanismus delegování, ale může působit jako mechanismus vysílání. Například při vyhodnocování výrazu model SDM funguje jako mechanismus vysílání pro oznamování všech DEs, které mohou spustit kód v zadaném vlákně. Podobně platí, že když SDM přijme událost zastavení, vysílá do programů, které by měly přestat běžet. Při volání tohoto kroku se všesměrové vysílání SDM do programů, které můžou dál používat. Zarážky se také vysílá do každé DE.

 Model SDM nesleduje aktuální program, vlákno nebo blok zásobníku. Informace o procesu, programu a vlákně jsou odesílány do SDM ve spojení s konkrétními událostmi ladění.

## <a name="see-also"></a>Viz také
- [Ladicí stroj](../../extensibility/debugger/debug-engine.md)
- [Komponenty ladicího programu](../../extensibility/debugger/debugger-components.md)
- [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md)
