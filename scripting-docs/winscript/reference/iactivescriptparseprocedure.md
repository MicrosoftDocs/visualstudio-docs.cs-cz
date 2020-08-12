---
title: IActiveScriptParseProcedure | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 3567a22eac2ad270739e62e0f0fb9914bdf4a9ec
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144568"
---
# <a name="iactivescriptparseprocedure"></a>IActiveScriptParseProcedure
Pokud skriptovací stroj Windows umožňuje, aby text zdrojového kódu pro procedury byly přidány do skriptu, implementuje `IActiveScriptParseProcedure` rozhraní. Pro interpretované skriptovací jazyky, které nemají nezávislé vývojové prostředí, jako je například VBScript, to poskytuje alternativní mechanizmus (jiný než `IActiveScriptParse` nebo `IPersist` *) pro přidání procedur skriptu do oboru názvů.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
  
|Metoda|Popis|
|-|-|
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|Analyzuje daný postup kódu a přidá proceduru do oboru názvů.|  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní aktivních skriptů](../../winscript/reference/active-script-interfaces.md)