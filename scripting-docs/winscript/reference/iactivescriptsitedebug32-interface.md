---
title: Rozhraní IActiveScriptSiteDebug32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 2a55161f76fcd98b52ddb769c640aca0e903239b
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835261"
---
# <a name="iactivescriptsitedebug32-interface"></a>IActiveScriptSiteDebug32 – rozhraní
Inteligentní hostitelé implementují `IActiveScriptSiteDebug32` rozhraní k provádění správy dokumentů a k účasti na ladění. `IActiveScriptSite`Objekt obvykle poskytuje implementaci `IActiveScriptSiteDebug32` rozhraní. Pokud je to hotovo, zavolejte `IActiveScriptSite::QueryInterface` metodu pro získání `IActiveScriptSiteDebug32` rozhraní.  
  
 Kromě metod zděděných z `IUnknown` `IActiveScriptSiteDebug32` rozhraní zpřístupňuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|Vrátí objekt aplikace ladění přidružený k tomuto webu skriptu.|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|K delegování používá jazykový modul `IDebugCodeContext::GetSourceContext` .|