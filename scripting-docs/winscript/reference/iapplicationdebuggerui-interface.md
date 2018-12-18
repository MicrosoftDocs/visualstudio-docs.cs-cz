---
title: Iapplicationdebuggerui – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IApplicationDebuggerUI interface
ms.assetid: b8828817-ca24-4012-802c-7dcaeea65dc8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbaa04f6790ffc4d80447a6745ca82cc8dba6802
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793668"
---
# <a name="iapplicationdebuggerui-interface"></a>IApplicationDebuggerUI – rozhraní
Implementované ladicí program integrované vývojové prostředí (IDE) (kromě `IApplicationDebugger`) umožnit externí komponenta větší kontrolu nad uživatelské rozhraní (UI) ladicího programu.  
  
 Kromě metod zděděno z `IUnknown`, `IApplicationDebuggerUI` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|Otevře okno obsahující zadanou ladění dokumentu, který má nejvyšší v ladicím programu uživatelské rozhraní.|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|Zobrazí se okno obsahující kontext daného dokumentu, který má nejvyšší v uživatelském rozhraní ladicího programu a posune okno kontextu.|