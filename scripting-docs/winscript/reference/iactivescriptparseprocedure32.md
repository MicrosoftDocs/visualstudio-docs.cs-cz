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
ms.openlocfilehash: 1993cbef966a4d73a2a3ed55c3317db444702232
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574878"
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
Pokud skriptovací stroj systému Windows umožňuje přidat do skriptu text zdrojového kódu pro procedury, implementuje rozhraní `IActiveScriptParseProcedure32`. V případě interpretovaných skriptovacích jazyků, které nemají nezávislé vývojové prostředí, jako je například VBScript, toto poskytuje alternativní mechanismus (jiný než `IActiveScriptParse32` nebo `IPersist` *) pro přidání procedur skriptu do oboru názvů.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
  
|||  
|-|-|  
|Metoda|Popis|  
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|Analyzuje daný postup kódu a přidá proceduru do oboru názvů.|  
  
## <a name="see-also"></a>Viz také:  
 [Rozhraní aktivních skriptů](../../winscript/reference/active-script-interfaces.md)