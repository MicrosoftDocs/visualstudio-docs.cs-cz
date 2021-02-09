---
title: Rozhraní poskytovatele symbolů | Microsoft Docs
description: Tento článek obsahuje odkazy na popisy rozhraní pro zpracování symbolů pro sadu Visual Studio SDK, které vyhodnotí proměnné v zásobníku volání během režimu přerušení.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f5c2204a1f8c4bef17256e98ed04dcf4b195c3aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850818"
---
# <a name="symbol-provider-interfaces"></a>Rozhraní poskytovatele symbolů
Níže jsou uvedené rozhraní pro zpracování symbolů pro [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)] .

## <a name="discussion"></a>Diskuse
 Tato rozhraní se používají k vyhodnocení proměnných v zásobníku volání během režimu přerušení. Jsou implementované pouze pro poskytovatele symbolů Common Language Runtime (SP).

|Rozhraní|Implementuje|Description|
|---------------|--------------------|-----------------|
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|Představuje adresu položky.|
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|Představuje adresu položky, která poskytuje přístup k ID procesu.|
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|Představuje symbol pole nebo typ pole.|
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|Představuje symbol třídy nebo typ třídy.|
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|Představuje poskytovatele symbolů COM+ s metodami, které jsou specifické pro spravovaný kód.|
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|Představuje poskytovatele symbolů COM+ s metodami, které jsou specifické pro spravovaný kód a rozšiřuje **IDebugComPlusSymbolProvider**.|
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|Představuje symbol nebo typ, který je kontejnerem pro jiné symboly nebo typy.|
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|Představuje vlastní atribut, který může být připojen k symbolu.|
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|Představuje dotaz pro vlastní atributy pro metodu nebo typ.|
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|Poskytuje přístup k vlastním atributům na symbolu.|
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|Základní rozhraní pro jakýkoli typ, který lze určit za běhu.|
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|Představuje dynamické pole pro objekt [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .|
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|Představuje typ výčtu.|
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|SP|Rozšiřuje typy dostupných polí na podporu obecných kódů spravovaného kódu.|
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|Základní třída pro všechna pole; představuje popis symbolu nebo typu.|
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|Představuje definici pole pro obecný typ spravovaného kódu.|
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|Představuje instanci pole pro obecný typ spravovaného kódu.|
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|Představuje parametr pro obecný typ spravovaného kódu.|
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|Představuje metodu.|
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|Představuje volitelný modifikátor ladění.|
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|Představuje ukazatel.|
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|Představuje hodnotu výčtu primitivního typu z rozhraní [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .|
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|Představuje vlastnost třídy spravovaného kódu, kterou lze získat nebo nastavit.|
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|Představuje poskytovatele symbolů, který poskytuje symboly a typy.|
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|Představuje poskytovatele symbolů s přímým přístupem k rozhraním metadat a základních symbolů.|
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|Představuje schopnost vytvořit pole, které představuje typ.|
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|Rozšiřuje **IDebugTypeFieldBuilder** tak, aby bylo možné vytvářet typy polí.|
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|Představuje kolekci objektů [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .|
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|Představuje kolekci objektů [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) .|
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|Představuje kolekci objektů [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .|

## <a name="see-also"></a>Viz také
- [Referenční informace k rozhraním API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
