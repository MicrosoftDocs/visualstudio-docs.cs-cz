---
title: IEnumDebugAddresses | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2373a26da1f6c3b327bea3a6f2402beb7d8bce45
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196149"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní představuje kolekci objektů, které implementují rozhraní [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugAdresses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Toto rozhraní je implementováno zprostředkovatelem symbolů pro poskytování sad objektů, které implementují rozhraní [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) . Všimněte si, že se nejedná o standardní výčet modelu COM z důvodu přítomnosti metody [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) .  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Toto rozhraní je vráceno pomocí [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) a [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 Toto rozhraní implementuje následující metody.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Další](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Načte další sadu objektů [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) z výčtu.|  
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Přeskočí zadaný počet položek.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Obnoví výčet na první položku.|  
|[Klonování](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Načte kopii aktuálního výčtu.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Načte počet položek ve výčtu.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní obvykle používá ladicí stroj k určení vhodné adresy pro vyhodnocení výrazu.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: SH. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní poskytovatele symbolů](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
