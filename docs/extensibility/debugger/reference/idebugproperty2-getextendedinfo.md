---
description: Získá Rozšířené informace o vlastnosti.
title: 'IDebugProperty2:: GetExtendedInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 004c7d545dbaaa20016fd94febe999420305fc7a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171496"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
Získá Rozšířené informace o vlastnosti.

## <a name="syntax"></a>Syntaxe

```cpp
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

## <a name="parameters"></a>Parametry
`guidExtendedInfo`\
pro Identifikátor GUID, který určuje typ rozšířených informací, které mají být načteny. Podrobnosti najdete v části poznámky.

`pExtendedInfo`\
mimo Vrátí `VARIANT` kód (C++) nebo objekt (C#), který lze použít k načtení informací rozšířených vlastností. Například tento parametr může vracet `IUnknown` rozhraní, které lze dotazovat pro rozhraní [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) . Podrobnosti najdete v části poznámky.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . jinak vrátí kód chyby. Vrátí `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` , zda nejsou k dispozici žádné rozšířené informace k načtení.

## <a name="remarks"></a>Poznámky
 Tato metoda existuje pro účely načítání informací, které nezpůsobují načtení, voláním metody [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) .

 Následující identifikátory GUID jsou obvykle rozpoznávány touto metodou (hodnoty GUID jsou zadány pro jazyk C#, protože název není k dispozici v žádném sestavení). Pro interní použití lze vytvořit další identifikátory GUID.

|Název|Identifikátor GUID|Popis|
|----------|----------|-----------------|
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|Vrátí `IUnknown` rozhraní k dokumentu. Rozhraní [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) se obvykle dá získat z tohoto `IUnknown` rozhraní.|
|guidCodeContext|{e2fc65e-56ce-11d1-b528-00aax004a8797}|Vrátí `IUnknown` rozhraní do kontextu dokumentu. Rozhraní [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) se obvykle dá získat z tohoto `IUnknown` rozhraní.|
|guidCustomViewerSupported|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Vrátí řetězec obsahující CLSID vlastního prohlížeče, který je obvykle implementován vyhodnocovacím filtrem výrazů.|
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|Vrátí 32-bit číslo představující požadované číslo slotu, pokud tato vlastnost představuje místní adresu spravovaného kódu.|
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Vrátí řetězec obsahující signaturu proměnné přidružené k objektu vlastnosti.|

## <a name="see-also"></a>Viz také
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
