---
title: IDebugContainerField::EnumFields | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 49874de9166310fc4b9a887fd1fc6d6355682c7a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942683"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Vytvoří čítač pro pole kontejneru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumFields(   
   FIELD_KIND         dwKindFilter,  
   FIELD_MODIFIERS    dwModifiersFilter,  
   LPCOLESTR          pszNameFilter,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumFields(  
   enum_ FIELD_KIND      dwKindFilter,   
   enum_ FIELD_MODIFIERS dwModifiersFilter,   
   string                pszNameFilter,   
   NAME_MATCH            nameMatch,   
   out IEnumDebugFields  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwKindFilter`  
 [in] Kombinace [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) konstanty, které vyberte pole pro provedení výčtu. Typy pole můžete popsat typy úložišť, jako je například třídy nebo primitivní nebo konkrétní informace, jako jsou místní, parametr nebo ukazatel "this".  
  
 `dwModifiersFilter`  
 [in] Kombinace [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) konstanty, které vyberte pole pro provedení výčtu. Modifikátory pole může být přístupová oprávnění, jako jsou veřejné, privátní nebo úložiště informace, jako je například virtuální, statické nebo konečné.  
  
 `pszNameFilter`  
 [in] Název pole, které chcete vytvořit výčet. To může být hodnota null, pokud všechna pole se mají vrátit.  
  
 `nameMatch`  
 [in] Hodnota z [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) výčet, který určuje, jestli hledání je velká a malá písmena, nebo ne.  
  
 `ppEnum`  
 [out] Vrátí [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objekt představující seznam polí. Vrátí hodnotu null, pokud nejsou žádná pole.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí hodnotu S_OK nebo S_FALSE, pokud nejsou žádná pole. V opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 `dwKindFilter`, `dwModifiersFilter`, A `pszNameFilter` parametry je možné kombinovat například, chcete-li vybrat všechny veřejné virtuální metody s názvem "MyMethod".  
  
## <a name="see-also"></a>Viz také  
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)