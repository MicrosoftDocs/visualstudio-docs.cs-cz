---
title: Rozhraní poskytovatele symbolů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7929ba36c76f0db1cabab087afe3590de509efff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715839"
---
# <a name="symbol-provider-interfaces"></a>Rozhraní poskytovatele symbolů
Následují rozhraní pro zpracování symbolů [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]pro rozhraní .

## <a name="discussion"></a>Diskuse
 Tato rozhraní se používají k vyhodnocení proměnných v zásobníku volání během režimu přerušení. Jsou implementovány pouze pro zprostředkovatele symbolů běžného běhu jazyka (SP).

|Rozhraní|Implementováno|Popis|
|---------------|--------------------|-----------------|
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|Sp|Představuje adresu položky.|
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|Sp|Představuje adresu položky, poskytující přístup k ID procesu.|
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|Sp|Představuje symbol pole nebo typ pole.|
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|Sp|Představuje symbol třídy nebo typ třídy.|
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|Sp|Představuje poskytovatele symbolu MODELU COM+ s metodami, které jsou specifické pro spravovaný kód.|
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|Sp|Představuje zprostředkovatele symbolu MODELU COM+ s metodami, které jsou specifické pro spravovaný kód a rozšiřuje **IDebugComPlusSymbolProvider**.|
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|Sp|Představuje symbol nebo typ, který je kontejner pro jiné symboly nebo typy.|
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|Sp|Představuje vlastní atribut, který lze připojit ke symbolu.|
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|Sp|Představuje dotaz pro vlastní atributy na metodu nebo typ.|
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|Sp|Poskytuje přístup k vlastním atributům na symbolu.|
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|Sp|Základní rozhraní pro libovolný typ, který lze určit za běhu.|
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|Sp|Představuje dynamické pole pro objekt [IDebugBinder.](../../../extensibility/debugger/reference/idebugbinder.md)|
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|Sp|Představuje typ výčtu.|
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|Sp|Rozšiřuje typy dostupných polí pro podporu obecných typů spravovaného kódu.|
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|Sp|Základní třída pro všechna pole; představuje popis symbolu nebo typu.|
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|Sp|Představuje definici pole pro obecný typ spravovaného kódu.|
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|Sp|Představuje instanci pole pro obecný typ spravovaného kódu.|
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|Sp|Představuje parametr pro obecný typ spravovaného kódu.|
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|Sp|Představuje metodu.|
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|Sp|Představuje ladění volitelné modifikátor.|
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|Sp|Představuje ukazatel.|
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|Sp|Představuje primitivní hodnotu výčtu typu z rozhraní [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)|
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|Sp|Představuje vlastnost třídy spravovaného kódu, která může být get nebo set.|
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|Sp|Představuje zprostředkovatele symbol, který poskytuje symboly a typy.|
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|Sp|Představuje zprostředkovatele symbolů s přímým přístupem k metadatům a rozhraním základního symbolu.|
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|Sp|Představuje schopnost vytvořit pole, které představuje typ.|
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|Sp|Rozšiřuje **IDebugTypeFieldBuilder,** aby bylo možné vytvářet typy polí.|
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|Sp|Představuje kolekci [iDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objekty.|
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|Sp|Představuje kolekci [iDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) objekty.|
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|Sp|Představuje kolekci [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objekty.|

## <a name="see-also"></a>Viz také
- [Referenční informace k rozhraním API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
