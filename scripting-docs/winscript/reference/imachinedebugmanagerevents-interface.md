---
title: Imachinedebugmanagerevents – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerEvents interface
ms.assetid: 468de2f4-49e0-4f6f-ba0c-0f5f6832c092
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 369dc8d182efe7bf9697454d0e4b1c9c1a10c027
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794442"
---
# <a name="imachinedebugmanagerevents-interface"></a>IMachineDebugManagerEvents – rozhraní
Signály změny v běžícím seznam aplikací, které spravuje pomocí nástroje machine manager ladění. Toto rozhraní lze ladicí program IDE pro zobrazení seznamu dynamických aplikací.  
  
 Kromě metod zděděno z `IUnknown`, `IMachineDebugManagerEvents` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|Zpracovává událost při přidání aplikace do spuštění seznam aplikací.|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|Zpracovává událost, pokud aplikace je odebrán z spuštění seznam aplikací.|