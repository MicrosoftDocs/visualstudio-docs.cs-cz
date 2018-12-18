---
title: Idisperror – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDispError interface
ms.assetid: 3dc7b55e-94ba-4669-b20a-1e011f2d07cf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9f139d317db5aa00f03f8e9abd71020e5ff35b03
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794586"
---
# <a name="idisperror-interface"></a>IDispError – rozhraní
Poskytuje podrobné kontextové informace o chybě.  
  
> [!NOTE]
>  Toto rozhraní není implementováno.  
  
 Kromě metod zděděno z `IUnknown`, `IDispError` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|Načte konkrétní typ informace o chybě.|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|Načte další `IDispError` objektu.|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|Načte kód chyby z `IDispError` objektu.|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|Vrátí identifikátor programový závislých na jazyku pro třídu nebo aplikaci, která vyvolá chybu.|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|Vrátí cestu k souboru nápovědy a ID kontextu téma, které popisuje chybu, pokud je to možné.|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|Vrátí textový popis chyby.|