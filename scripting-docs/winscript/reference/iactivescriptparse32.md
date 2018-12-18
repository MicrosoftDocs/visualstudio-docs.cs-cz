---
title: IActiveScriptParse32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c39c14aa-beb7-4eca-8b8c-2181da1c2e3e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 688a89515179912c1ed3ac815f0febf50ab4db0f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793377"
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
Pokud skript Windows modul umožňuje nezpracovaný text kódu skriptlety pro přidání do skriptu nebo umožňuje výraz text, který má být vyhodnocovány v době běhu, implementuje `IActiveScriptParse32` rozhraní. Pro Interpretovaný skriptovací jazyky, které mají žádné nezávislé pro tvorbu prostředí, například VBScript, to poskytuje alternativní mechanismus (jiné než `IPersist*`) získat kód skriptu do skriptovacího stroje a připojit fragmenty skriptu do různých objektu události.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|Přidá skriptlet kód skriptu.|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|Inicializuje skriptovacího stroje.|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|Analyzuje skriptlet daného kódu, přidávání deklarace do oboru názvů a vyhodnocení kódu podle potřeby.|