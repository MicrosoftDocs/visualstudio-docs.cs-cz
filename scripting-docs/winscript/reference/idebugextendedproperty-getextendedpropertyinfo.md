---
title: 'Idebugextendedproperty –:: GetExtendedPropertyInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExtendedProperty.GetExtendedPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugExtendedProperty::GetExtendedPropertyInfo
ms.assetid: 56edf538-5082-4653-82b6-e6640d6f61ba
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77167c46e02bcf2bf5d3ce5836ad5de103176e93
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576378"
---
# <a name="idebugextendedpropertygetextendedpropertyinfo"></a>IDebugExtendedProperty::GetExtendedPropertyInfo
Načte rozšířené informace pro rozšířenou vlastnost, což jsou další informace, než jednodušší `IDebugProperty`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetExtendedPropertyInfo(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   ExtendedDebugPropertyInfo*  pExtendedPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFieldSpec`  
 pro Určuje konstanty EX_DBGPROP_INFO_FLAGS, které určují, která pole se mají vyplnit ve struktuře `ExtendedDebugPropertyInfo`.  
  
 `nRadix`  
 pro Číselná soustava, která se má použít při interpretaci libovolných číselných informací.  
  
 `pExtendedPropertyInfo`  
 mimo Vrátí strukturu `ExtendedDebugPropertyInfo`, která popisuje vlastnost.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací platný `HRESULT`, obvykle `S_OK`.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní idebugextendedproperty –](../../winscript/reference/idebugextendedproperty-interface.md)  
 [EX_DBGPROP_INFO_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)    
 [ExtendedDebugPropertyInfo – struktura](../../winscript/reference/extendeddebugpropertyinfo-structure.md)