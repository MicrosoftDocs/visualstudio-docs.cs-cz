---
title: Iactivescriptparseprocedureold – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld interface
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99cff9cd4d04c5d25489b6cc4c9b9af93792dc2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793386"
---
# <a name="iactivescriptparseprocedureold-interface"></a>IActiveScriptParseProcedureOld – rozhraní
Umožňuje zdrojový kód text postupy pro přidání do skriptu. Pro Interpretovaný skriptovací jazyky, které nemají nezávislé pro tvorbu prostředí, například VBScript, to poskytuje alternativní mechanismus (jiné než `IActiveScriptParse` nebo `IPersist*`) postupy skriptu přidat do oboru názvů.  
  
> [!NOTE]
>  Toto rozhraní je zastaralé pro `IActiveScriptParseProcedure` rozhraní.  
  
## <a name="methods"></a>Metody  
 Kromě metod zděděno z `IUnknown`, `IActiveScriptParseProcedureOld` rozhraní poskytuje následující metody.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Analyzuje postup daného kódu a postup přidá do oboru názvů.|  
  
## <a name="see-also"></a>Viz také  
 [Iactivescriptparseprocedure –](../../winscript/reference/iactivescriptparseprocedure.md)