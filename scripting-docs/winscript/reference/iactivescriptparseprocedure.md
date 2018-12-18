---
title: Iactivescriptparseprocedure – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParseProcedure interface
ms.assetid: 741a35bb-5b92-489e-ba8a-a406b42125fc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77aaa60942855a71f7d71037fbefb06462336a13
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793359"
---
# <a name="iactivescriptparseprocedure"></a>IActiveScriptParseProcedure
Pokud modul Windows Script umožňuje zdrojový kód text postupy pro přidání do skriptu, implementuje `IActiveScriptParseProcedure` rozhraní. Pro Interpretovaný skriptovací jazyky, které mají žádné nezávislé pro tvorbu prostředí, například VBScript, to poskytuje alternativní mechanismus (jiné než `IActiveScriptParse` nebo `IPersist`*) Chcete-li přidat skript procedury do oboru názvů.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|||  
|-|-|  
|Metoda|Popis|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|Analyzuje postup daného kódu a postup přidá do oboru názvů.|  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní aktivních skriptů](../../winscript/reference/active-script-interfaces.md)