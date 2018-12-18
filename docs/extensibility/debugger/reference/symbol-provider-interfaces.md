---
title: Symbolů poskytovatele rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 798334058a89199e1e40e023e0b7f46d13c36997
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131298"
---
# <a name="symbol-provider-interfaces"></a>Zprostředkovatel rozhraní symbol
Následují rozhraní Symbol zpracování pro aplikaci [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].  
  
## <a name="discussion"></a>Diskusní  
 Tato rozhraní se používají k vyhodnocení proměnné v zásobníku volání při režimu pozastavení. Implementují se pouze pro běžné language runtime symbol zprostředkovatele (SP).  
  
|Rozhraní|Implementované|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|Představuje adresu položky.|  
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|Představuje adresu položku, zajištění přístupu k ID procesu.|  
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|Představuje na symbol pole nebo typ pole.|  
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|Představuje symbol třídy nebo typu třídy.|  
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|Představuje symbol zprostředkovatele modelu COM + s metodami, které jsou specifické pro spravovaný kód.|  
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|Představuje symbol zprostředkovatele modelu COM + s metodami, které jsou specifické pro spravovaný kód a rozšiřuje **IDebugComPlusSymbolProvider**.|  
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|Představuje symbol nebo typ, který je kontejner pro další symboly nebo typy.|  
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|Představuje vlastní atribut, který lze k symbolu.|  
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|Představuje dotaz pro vlastní atributy, metoda nebo typu.|  
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|Poskytuje přístup k vlastní atributy na symbol.|  
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|Základní rozhraní pro žádný typ, který můžete určit za běhu.|  
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|Představuje dynamické pole pro [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) objektu.|  
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|Představuje typ výčtu.|  
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|SP|Rozšiřuje typy polí k dispozici pro podporu obecné spravovaného kódu.|  
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|Základní třída pro všechna pole; představuje popis symbolu nebo typu.|  
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|Představuje definici pole pro obecný typ spravovaného kódu.|  
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|Představuje instanci pole pro obecný typ spravovaného kódu.|  
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|Reprezentuje parametr pro obecný typ spravovaného kódu.|  
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|Představuje metodu.|  
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|Představuje volitelný modifikátor ladění.|  
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|Představuje ukazatel.|  
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|Reprezentuje hodnotu primitivní typ výčtu ze [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) rozhraní.|  
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|Reprezentuje vlastnost třídy spravovaného kódu, která může být get nebo nastavit.|  
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|Představuje zprostředkovatele symbol, který obsahuje typy a symboly.|  
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|Představuje zprostředkovatele symbol s přímým přístupem do metadat a základní rozhraní symbol.|  
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|Představuje schopnost vytvářet pole, které představuje typ.|  
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|Rozšiřuje **IDebugTypeFieldBuilder** mohli vytvořit typy polí.|  
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|Představuje kolekci [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objekty.|  
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|Představuje kolekci [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) objekty.|  
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|Představuje kolekci [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objekty.|  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace ke knihovně API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)