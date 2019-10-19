---
title: Rozhraní Iactivescriptparseprocedureold – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 4558a0cab2aea9b56db2759bb80b1287cd33ce87
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571422"
---
# <a name="iactivescriptparseprocedureold-interface"></a>IActiveScriptParseProcedureOld – rozhraní
Umožňuje přidat do skriptu text zdrojového kódu pro procedury. V případě interpretace skriptovacích jazyků, které nemají nezávislé vývojové prostředí, jako je například VBScript, tato možnost poskytuje alternativní mechanismus (jiný než `IActiveScriptParse` nebo `IPersist*`) pro přidání procedur skriptu do oboru názvů.  
  
> [!NOTE]
> Toto rozhraní je zastaralé namísto rozhraní `IActiveScriptParseProcedure`.  
  
## <a name="methods"></a>Metody  
 Kromě metod zděděných z `IUnknown` rozhraní `IActiveScriptParseProcedureOld` zpřístupňuje následující metody.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Analyzuje daný postup kódu a přidá proceduru do oboru názvů.|  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)