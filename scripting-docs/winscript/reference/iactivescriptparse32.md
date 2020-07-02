---
title: IActiveScriptParse32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c39c14aa-beb7-4eca-8b8c-2181da1c2e3e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 568feacfe75de22a330c892a44fa4f4f6fd0e3b8
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835313"
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
Pokud skriptovací stroj Windows umožňuje přidat nezpracovaný textový kód skriptlety do skriptu nebo umožňuje vyhodnotit text výrazu za běhu, implementuje `IActiveScriptParse32` rozhraní. V případě interpretace skriptovacích jazyků, které nemají nezávislé vývojové prostředí, jako je například VBScript, tato akce poskytuje alternativní mechanizmus (jiný než `IPersist*` ) k získání kódu skriptu do skriptovacího stroje a k připojení fragmentů skriptů k různým událostem objektu.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|Přidá do skriptu kód skriptletu.|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|Inicializuje skriptovací modul.|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|Analyzuje daný kód skriptletu, přidává deklarace do oboru názvů a podle potřeby vyhodnocuje kód.|