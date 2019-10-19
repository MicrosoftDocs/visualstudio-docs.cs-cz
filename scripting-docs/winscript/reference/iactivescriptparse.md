---
title: IActiveScriptParse | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 81f64352c15dce233058d49b70e35da7e2238688
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561650"
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
Pokud skriptovací stroj Windows umožňuje přidat nezpracovaný textový kód skriptlety do skriptu nebo umožňuje vyhodnotit text výrazu za běhu, implementuje rozhraní `IActiveScriptParse`. V případě interpretace skriptovacích jazyků, které nemají nezávislé vývojové prostředí, jako je například VBScript, je k dispozici alternativní mechanizmus (jiný než `IPersist*`) k získání kódu skriptu do skriptovacího stroje a k připojení fragmentů skriptů k různým událostem objektu. .  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Inicializuje skriptovací modul.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Přidá do skriptu kód skriptletu.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Analyzuje daný kód skriptletu, přidává deklarace do oboru názvů a podle potřeby vyhodnocuje kód.|  
  
## <a name="see-also"></a>Viz také:  
 [Rozhraní aktivních skriptů](../../winscript/reference/active-script-interfaces.md)