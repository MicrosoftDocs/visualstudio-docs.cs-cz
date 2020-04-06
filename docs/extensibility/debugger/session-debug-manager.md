---
title: Správce ladění relací | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712875"
---
# <a name="session-debug-manager"></a>Správce ladění relace
Správce ladění relace (SDM) spravuje libovolný počet ladicích strojů (DE), které ladí libovolný počet programů ve více procesech v libovolném počtu počítačů. Kromě toho, že multiplexor ladicí modul, SDM poskytuje jednotné zobrazení relace ladění ide.

## <a name="session-debug-manager-operation"></a>Operace správce ladění relace
 Správce ladění relace (SDM) spravuje DE. V počítači může být současně spuštěno více než jeden ladicí modul. Chcete-li multiplexovat DEs, SDM zalomí počet rozhraní z DE a zpřístupňuje je ide jako jediné rozhraní.

 Chcete-li zvýšit výkon, některá rozhraní nejsou multiplexní. Místo toho se používají přímo z DE a volání těchto rozhraní neprocházejí SDM. Například rozhraní používaná s kontexty paměti, kódu a dokumentu nejsou multiplexována, protože odkazují na konkrétní instrukce, paměť nebo dokument v určitém programu laděné určitým DE. Do této úrovně komunikace nemusí být zapojen žádný jiný de.

 To neplatí pro všechny kontexty. Volání rozhraní kontextu vyhodnocení výrazu projít SDM. Během vyhodnocení výrazu SDM zalomí rozhraní [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) které poskytuje ide, protože při vyhodnocení tohoto výrazu může zahrnovat více DEs, které jsou ladění programů ve stejném procesu, který může být spuštěn ve stejném vlákně.

 SDM obvykle funguje jako mechanismus delegování, ale může fungovat jako mechanismus vysílání. Například během vyhodnocení výrazu SDM funguje jako mechanismus vysílání upozornit všechny DE, které mohou spustit kód v zadaném vlákně. Podobně když SDM obdrží událost zastavení, vysílá do programů, které by měly přestat spouštět. Při volání kroku sm vysílání do programů, které mohou pokračovat v běhu. Zarážky jsou také vysílány do každého DE.

 SDM nesleduje aktuální program, vlákno nebo rámec zásobníku. Informace o procesu, programu a vlákně jsou odesílány do sdm ve spojení s konkrétními událostmi ladění.

## <a name="see-also"></a>Viz také
- [Ladicí modul](../../extensibility/debugger/debug-engine.md)
- [Součásti ladicího programu](../../extensibility/debugger/debugger-components.md)
- [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md)
