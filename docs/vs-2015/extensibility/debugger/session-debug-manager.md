---
title: Správce ladění relace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9fd7c7555c19f850a15161f6fba00b1184621a9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157826"
---
# <a name="session-debug-manager"></a>Správce ladění relace
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Správce ladění relace (SDM) spravuje libovolný počet ladicích modulů (DE) ladění libovolného počtu programů ve více procesech na libovolném počtu počítačů. Kromě toho, že se jedná o multiplexor ladicího stroje, model SDM poskytuje jednotný přehled o relaci ladění IDE.  
  
## <a name="session-debug-manager-operation"></a>Operace Správce ladění relace  
 Správce ladění relace (SDM) spravuje DE. V počítači může být spuštěno více než jeden ladicí modul současně. Pro multiplexování algoritmu DEs zalomí model SDM mnoho rozhraní z algoritmu DEs a zpřístupňuje je rozhraní IDE jako jediné rozhraní.  
  
 Aby se zvýšil výkon, některá rozhraní se nemultiplexují. Místo toho se používají přímo z DE a volání do těchto rozhraní neprojde přes SDM. Například rozhraní používaná s kontexty paměti, kódu a dokumentu nejsou multiplexovaná, protože odkazují na konkrétní instrukci, paměť nebo dokument v určitém programu, který je laděn specifickým DE. V této úrovni komunikace není potřeba žádný jiný DE.  
  
 To není pravdivé u všech kontextů. Volání rozhraní kontextu vyhodnocení výrazu procházejí přes SDM. Během vyhodnocování výrazu model SDM zabalí rozhraní [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , které poskytuje rozhraní IDE, protože při vyhodnocování tohoto výrazu může zahrnovat několik des, které ladí programy ve stejném procesu, který může být spuštěn ve stejném vlákně.  
  
 SDM obvykle funguje jako mechanismus delegování, ale může působit jako mechanismus vysílání. Například při vyhodnocování výrazu model SDM funguje jako mechanismus vysílání pro oznamování všech DEs, které mohou spustit kód v zadaném vlákně. Podobně platí, že když SDM přijme událost zastavení, vyšle všesměrové vysílání všem programům, které by měly přestat běžet. Při volání tohoto kroku se všesměrové vysílání SDM do všech programů, které můžou dál používat. Zarážky se také vysílá do každé DE.  
  
 Model SDM nesleduje aktuální program, vlákno nebo blok zásobníku. Informace o procesu, programu a vlákně jsou odesílány do SDM ve spojení s konkrétními událostmi ladění.  
  
## <a name="see-also"></a>Viz také  
 [Ladicí stroj](../../extensibility/debugger/debug-engine.md)   
 [Komponenty ladicího programu](../../extensibility/debugger/debugger-components.md)   
 [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md)
