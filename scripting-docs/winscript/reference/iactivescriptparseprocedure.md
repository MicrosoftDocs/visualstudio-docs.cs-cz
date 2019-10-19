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
ms.openlocfilehash: c20947a125766547565d99c5762c20e23652da1a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561668"
---
# <a name="iactivescriptparseprocedure"></a>IActiveScriptParseProcedure
Pokud skriptovací stroj systému Windows umožňuje přidat do skriptu text zdrojového kódu pro procedury, implementuje rozhraní `IActiveScriptParseProcedure`. V případě interpretovaných skriptovacích jazyků, které nemají nezávislé vývojové prostředí, jako je například VBScript, toto poskytuje alternativní mechanismus (jiný než `IActiveScriptParse` nebo `IPersist` *) pro přidání procedur skriptu do oboru názvů.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
  
|||  
|-|-|  
|Metoda|Popis|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|Analyzuje daný postup kódu a přidá proceduru do oboru názvů.|  
  
## <a name="see-also"></a>Viz také:  
 [Rozhraní aktivních skriptů](../../winscript/reference/active-script-interfaces.md)