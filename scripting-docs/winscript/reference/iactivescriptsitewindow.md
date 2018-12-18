---
title: Iactivescriptsitewindow – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteWindow interface
ms.assetid: 96d5c493-2c0b-47e2-848b-4a8dacdcd65c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3043a3c36b2f1ebdf439f22b1de19dd559e50cfa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793662"
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
Toto rozhraní je implementováno modulem hostitele, kteří podporují uživatelské rozhraní pro stejný objekt jako [iactivescriptsite –](../../winscript/reference/iactivescriptsite.md) . Nebude-li implementovat hostitelů, které nepodporují uživatelské rozhraní, jako jsou třeba servery, `IActiveScriptSiteWindow` rozhraní. Skriptovací stroj přistupuje toto rozhraní voláním `QueryInterface` z `IActiveScriptSite`.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Načte popisovač okna, které může fungovat jako vlastník místní okno, které musí být zobrazen skriptovacího stroje.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|Způsobí, že hostitel povolení nebo zakázání jeho hlavní okno a také všechny nemodální dialogová okna.|  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní aktivních skriptů](../../winscript/reference/active-script-interfaces.md)