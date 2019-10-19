---
title: 'Idebugproperty –:: Enummembers – | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.EnumMembers
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::EnumMembers
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f8c5f2cbb107d55e9ffe602cb7d3492701de10c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562416"
---
# <a name="idebugpropertyenummembers"></a>IDebugProperty::EnumMembers
Vytvoří výčet členů vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGSdwFieldSpec,  
   UINTnRadix,  
   REFIIDrefiid,  
   IEnumDebugPropertyInfo**ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFieldSpec`  
 pro Určuje `DBGPROP_INFO_FLAGS` konstanty, které určují, která pole ve výčtu struktur vlastností ladění mají být vyplněna.  
  
 `nRadix`  
 pro Číselná soustava, která se má použít při interpretaci libovolných číselných informací.  
  
 `refiid`  
 pro Tento identifikátor IID se předává pro filtrování čítače výčtu. IID je jedno z `IDebugPropertyEnumType` rozhraní, které dědí z `IDebugPropertyEnumType_All`.  
  
 `ppEnum`  
 mimo Vrátí rozhraní `IEnumDebugPropertyInfo`, které vytváří výčet vlastností členů.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací platný `HRESULT`, obvykle `S_OK`.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní idebugproperty –](../../winscript/reference/idebugproperty-interface.md)  
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)    
 @No__t_1 [rozhraní IDebugPropertyEnumType_All](../../winscript/reference/idebugpropertyenumtype-all-interface.md)  
 [IEnumDebugPropertyInfo – rozhraní](../../winscript/reference/ienumdebugpropertyinfo-interface.md)