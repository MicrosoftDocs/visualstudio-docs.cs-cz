---
title: IActiveScriptParseProcedure32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 387a856b-f5dc-4371-8620-bd574e046c2c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 8cd253db8cb63adad093b84c4bf47df07bd66d69
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793353"
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
Pokud modul Windows Script umožňuje zdrojový kód text postupy pro přidání do skriptu, implementuje `IActiveScriptParseProcedure32` rozhraní. Pro Interpretovaný skriptovací jazyky, které mají žádné nezávislé pro tvorbu prostředí, například VBScript, to poskytuje alternativní mechanismus (jiné než `IActiveScriptParse32` nebo `IPersist`*) Chcete-li přidat skript procedury do oboru názvů.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|||  
|-|-|  
|Metoda|Popis|  
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|Analyzuje postup daného kódu a postup přidá do oboru názvů.|  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní aktivních skriptů](../../winscript/reference/active-script-interfaces.md)