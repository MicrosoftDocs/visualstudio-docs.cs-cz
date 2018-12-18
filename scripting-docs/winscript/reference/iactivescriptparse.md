---
title: IActiveScriptParse – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParse interface
ms.assetid: 8c967d70-f582-4f64-9e79-49f40c4dcb7c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b0e3990ca43043909d99b309f58a344c1727450
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793341"
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
Pokud skript Windows modul umožňuje nezpracovaný text kódu skriptlety pro přidání do skriptu nebo umožňuje výraz text, který má být vyhodnocovány v době běhu, implementuje `IActiveScriptParse` rozhraní. Pro Interpretovaný skriptovací jazyky, které mají žádné nezávislé pro tvorbu prostředí, například VBScript, to poskytuje alternativní mechanismus (jiné než `IPersist*`) získat kód skriptu do skriptovacího stroje a připojit fragmenty skriptu do různých objektu události.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Inicializuje skriptovacího stroje.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Přidá skriptlet kód skriptu.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Analyzuje skriptlet daného kódu, přidávání deklarace do oboru názvů a vyhodnocení kódu podle potřeby.|  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní aktivních skriptů](../../winscript/reference/active-script-interfaces.md)