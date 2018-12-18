---
title: Isetnextstatement – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bdd71a427a8ef2c57684eef75a044d0cedf42415
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796239"
---
# <a name="isetnextstatement-interface"></a>ISetNextStatement – rozhraní
Toto rozhraní je implementováno modulem překladač umožňující správce ladění proces aktualizace aktuální příkaz. Je implementována z objektu rámce zásobníku a PDM získá toto rozhraní prostřednictvím QueryInterface.  
  
 rozhraní poskytuje metody, které jsou užitečné pro nastavení provádění bod, který určuje další příkaz má být proveden.  
  
 Kromě metod zděděno z `IUnknown`, `ISetNextStatement` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|Určuje, zda lze nastavit bod spuštění do zadaného umístění.|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|Nastaví bod spuštění do zadaného umístění.|