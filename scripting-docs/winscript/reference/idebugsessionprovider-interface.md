---
title: Idebugsessionprovider – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugSessionProvider interface
ms.assetid: 1b898423-7af9-44f5-8dda-987005309c99
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e61b1e5e794c68e34250f958cdda0f50b68334c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794295"
---
# <a name="idebugsessionprovider-interface"></a>IDebugSessionProvider – rozhraní
Primární rozhraní služby ladicí program IDE umožnit hostitele a jazyk iniciovala ladění. Navazuje na relaci ladění pro běžící aplikaci. Toto rozhraní je implementováno ladění správce počítače.  
  
 Kromě metod zděděno z `IUnknown`, `IDebugSessionProvider` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|Spustí relaci ladění pomocí zadané aplikace.|