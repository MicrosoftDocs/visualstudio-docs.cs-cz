---
title: IDebugProperty2::GetExtendedInfo | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9f6fd711a70c050a6f490a27a56eb860c84de867
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726945"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Získá rozšířené informace o vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetExtendedInfo (   
   REFGUID* guidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
```csharp  
int GetExtendedInfo (   
   ref Guid guidExtendedInfo,  
   out object pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `guidExtendedInfo`  
 [in] Identifikátor GUID, který určuje typ rozšířené informace, které se mají načíst. Podrobnosti najdete v části poznámky.  
  
 `pExtendedInfo`  
 [out] Vrátí `VARIANT` (C++) nebo objekt (C#), který slouží k načtení informací o rozšířené vlastnosti. Například může vrátit tento parametr `IUnknown` rozhraní, které je možné zadávat dotazy pro [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) rozhraní. Podrobnosti najdete v části poznámky.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby. Vrátí `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` Pokud neexistuje žádné rozšířené informace, které se mají načíst.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda existuje za účelem načtení informací, který se nepropůjčuje k načítají pomocí volání [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metody.  
  
 Následující identifikátory GUID jsou obvykle rozpoznána touto metodou (identifikátor GUID hodnoty jsou určené pro jazyk C# od název není k dispozici v libovolném sestavení). Další identifikátory GUID je vytvořit pro interní použití.  
  
|Název|GUID|Popis|  
|----------|----------|-----------------|  
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|Vrátí `IUnknown` rozhraní v dokumentu. Obvykle [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) rozhraní můžete získat z tohoto `IUnknown` rozhraní.|  
|guidCodeContext|{e2fc65e 56ce - 11d 1-b528-00aax004a8797}|Vrátí `IUnknown` rozhraní pro kontext dokumentu. Obvykle [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) rozhraní můžete získat z tohoto `IUnknown` rozhraní.|  
|guidCustomViewerSupported|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Vrátí řetězec obsahující identifikátor CLSID vlastní prohlížeč, většinou implementují moduly vyhodnocovače výrazů.|  
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|Vrátí 32-bit číslo reprezentující počet požadované slotu, je-li tato vlastnost představuje místních adres spravovaného kódu.|  
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Vrátí řetězec obsahující podpis proměnné přidružené k objektu vlastnosti.|  
  
## <a name="see-also"></a>Viz také  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)

