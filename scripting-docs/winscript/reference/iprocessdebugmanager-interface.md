---
title: Iprocessdebugmanager – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IProcessDebugManager interface
ms.assetid: b6ecb2bd-a4d1-4857-9232-036c154d0cb1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26c97fda6fc8657164e22d51eb041017a6239d98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794919"
---
# <a name="iprocessdebugmanager-interface"></a>IProcessDebugManager – rozhraní
Primární rozhraní pro správce ladění procesu. Toto rozhraní můžete vytvořit, přidat nebo odebrat virtuální aplikace z procesu. Můžete vytvořit výčet, aplikace vláken a rámce zásobníku.  
  
 Kromě metod zděděno z `IUnknown`, `IProcessDebugManager` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IProcessDebugManager::CreateApplication](../../winscript/reference/iprocessdebugmanager-createapplication.md)|Vytvoří nový objekt ladění aplikace pro tuto aplikaci.|  
|[IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)|Vrátí objekt výchozí aplikace pro aktuální proces.|  
|[IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)|Přidá aplikaci do seznamu Správce ladění počítače spuštěných aplikací.|  
|[IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)|Odebere aplikaci ze spuštění seznam aplikací.|  
|[IProcessDebugManager::CreateDebugDocumentHelper](../../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)|Vytvoří nového pomocníka dokumentu ladění pro tuto aplikaci.|