---
title: Idebugapplicationnode100 – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100 Interface
ms.assetid: 43966d4e-5f89-4a04-a08d-782347d00c2d
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af79614d38ef55776b660329f51931be70b7f52e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793896"
---
# <a name="idebugapplicationnode100-interface"></a>IDebugApplicationNode100 – rozhraní
`IDebugApplicationNode100` Rozhraní rozšiřuje funkce [idebugapplicationnode – rozhraní](../../winscript/reference/idebugapplicationnode-interface.md). Instance tohoto rozhraní můžete získat voláním QueryInterface na implementaci pro [idebugapplicationnode – rozhraní](../../winscript/reference/idebugapplicationnode-interface.md).  
  
> [!IMPORTANT]
>  Toto rozhraní je implementováno PDM v10.0 a větší. Nachází se v souboru activdbg100.h.  
  
## <a name="methods"></a>Metody  
 `IDebugApplicationNode100` Rozhraní poskytuje následující metody.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)|Získá text dokumenty, které jsou skrytý na základě zadaného filtru.|  
|[IDebugApplicationNode100::QueryIsChildNode](../../winscript/reference/idebugapplicationnode100-queryischildnode.md)|Určuje, zda zadaný dokument patří do jedné z podřízených uzlů tohoto uzlu.|  
|[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)|Nastaví filtr pro určitý [idebugapplicationnodeevents – rozhraní](../../winscript/reference/idebugapplicationnodeevents-interface.md) implementace. To umožňuje ladicí programy skriptu filtrovat generované kompilátorem podřízené uzly aplikace tak, aby PDM budou už odesílat události při vytváření nebo odebrat uzly. Ve výchozím nastavení budou odeslány všechny uzly.|