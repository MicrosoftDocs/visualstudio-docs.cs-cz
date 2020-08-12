---
title: IActiveScriptParseProcedure32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 387a856b-f5dc-4371-8620-bd574e046c2c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 71a22f422ff04e56a7aaa7a715641d190ade47bf
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144386"
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
Pokud skriptovací stroj Windows umožňuje, aby text zdrojového kódu pro procedury byly přidány do skriptu, implementuje `IActiveScriptParseProcedure32` rozhraní. Pro interpretované skriptovací jazyky, které nemají nezávislé vývojové prostředí, jako je například VBScript, to poskytuje alternativní mechanizmus (jiný než `IActiveScriptParse32` nebo `IPersist` *) pro přidání procedur skriptu do oboru názvů.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
  
|Metoda|Popis|
|-|-|
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|Analyzuje daný postup kódu a přidá proceduru do oboru názvů.|  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní aktivních skriptů](../../winscript/reference/active-script-interfaces.md)