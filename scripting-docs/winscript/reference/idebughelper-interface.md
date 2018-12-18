---
title: Idebughelper – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugHelper interface
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f0f70ecb8ead264d0d4b074f8fc1d9e3a6091eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794346"
---
# <a name="idebughelper-interface"></a>IDebugHelper – rozhraní
Slouží jako objekt factory pro objekt prohlížečů a jednoduchý spojovací body. Správce ladění procesu (PDM) implementuje toto rozhraní, které se spotřebovávají skriptovacích strojů.  
  
 Kromě metod zděděno z `IUnknown`, `IDebugHelper` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|Vrátí prohlížeči vlastností, které zabaluje hodnotu typu VARIANT.|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|Vrátí vlastnosti prohlížeče, který zabalí hodnotu typu VARIANT a umožňuje vlastní převod hodnot typu VARIANT nebo typy VARTYPE na řetězce.|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|Vrátí rozhraní událostí, které zabalí daného `IDispatch` objektu.|