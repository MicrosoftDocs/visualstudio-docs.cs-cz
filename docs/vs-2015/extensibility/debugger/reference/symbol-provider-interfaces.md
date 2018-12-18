---
title: Rozhraní poskytovatele symbolů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a37e27f6d7d1a9435f9519d3cecf359eb65fe204
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790770"
---
# <a name="symbol-provider-interfaces"></a>Rozhraní poskytovatele symbolů
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto jsou rozhraní zpracování symbolů pro [!INCLUDE[vsipsdk](../../../includes/vsipsdk-md.md)].  
  
## <a name="discussion"></a>Diskuse  
 Tato rozhraní se používají k vyhodnocení proměnné v zásobníku volání během režimu pozastavení. Tyto jsou implementované jenom pro běžné language runtime symbol poskytovatele (SP).  
  
|Rozhraní|Implementováno|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|Představuje adresu položky.|  
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|Představuje adresu položky, které umožňují přístup k ID procesu.|  
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|Představuje typ pole nebo pole symbolu.|  
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|Představuje symbol třídy nebo typu třídy.|  
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|Představuje zprostředkovatele symbol modelu COM + s metodami, které jsou specifické pro spravovaný kód.|  
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|Představuje zprostředkovatele symbol modelu COM + s metodami, které jsou specifické pro spravovaný kód a rozšiřuje **IDebugComPlusSymbolProvider**.|  
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|Představuje symbol nebo typ, který je kontejnerem pro další symboly nebo typy.|  
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|Představuje vlastní atribut, který lze připojit k symbolu.|  
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|Představuje dotaz pro vlastní atributy u metody nebo typu.|  
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|Poskytuje přístup k vlastní atributy na symbol.|  
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|Základní rozhraní pro libovolný typ, který se dá určit za běhu.|  
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|Představuje dynamické pole pro [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) objektu.|  
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|Představuje typ výčtu.|  
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|SP|Rozšiřuje typy dostupných polí pro podporu obecných typů spravovaného kódu.|  
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|Základní třída pro všechna pole; představuje popis symbol nebo typu.|  
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|Představuje definici pole pro obecný typ spravovaného kódu.|  
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|Představuje instanci pole pro obecný typ spravovaného kódu.|  
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|Reprezentuje parametr pro obecný typ spravovaného kódu.|  
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|Představuje metodu.|  
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|Představuje volitelný modifikátor ladění.|  
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|Představuje ukazatel.|  
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|Představuje hodnotu primitivní typ výčtu ze [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) rozhraní.|  
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|Reprezentuje vlastnost třídy spravovaný kód, který může být get nebo nastavit.|  
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|Představuje zprostředkovatele symbol, který obsahuje symboly a typy.|  
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|Představuje zprostředkovatele symbol s přímým přístupem do metadat a základní rozhraní symbol.|  
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|Představuje možnost vytvořit pole, které představuje typ.|  
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|Rozšiřuje **IDebugTypeFieldBuilder** budete moci vytvořit typy polí.|  
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|Představuje kolekci [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objekty.|  
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|Představuje kolekci [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) objekty.|  
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|Představuje kolekci [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objekty.|  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace ke knihovně API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)

