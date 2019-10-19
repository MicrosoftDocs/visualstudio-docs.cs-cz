---
title: IActiveScriptSiteWindow | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 1ee680a3d00c6736549b03ce8fee5593a7a8c5af
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575899"
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
Toto rozhraní je implementováno hostiteli, kteří podporují uživatelské rozhraní stejného objektu jako [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) . Hostitelé, kteří nepodporují uživatelské rozhraní, jako jsou servery, neimplementují rozhraní `IActiveScriptSiteWindow`. Skriptovací stroj přistupuje k tomuto rozhraní voláním `QueryInterface` z `IActiveScriptSite`.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Načte popisovač okna, který může fungovat jako vlastník automaticky otevíraného okna, který skriptovací stroj musí zobrazit.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|Způsobí, že hostitel povolí nebo zakáže hlavní okno a také všechna nemodální dialogová okna.|  
  
## <a name="see-also"></a>Viz také:  
 [Rozhraní aktivních skriptů](../../winscript/reference/active-script-interfaces.md)