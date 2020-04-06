---
title: IDebugProperty2::GetExtendedInfo | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34d6cd880ccae520bf000ad01b52223857f4f10f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721484"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
Získá rozšířené informace o vlastnosti.

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
[v] IDENTIFIKÁTOR GUID, který určuje typ rozšířených informací, které mají být načteny. Podrobnosti najdete v části Poznámky.

`pExtendedInfo`\
[out] Vrátí `VARIANT` (C++) nebo objekt (C#), který lze použít k načtení rozšířené informace o vlastnostech. Tento parametr může například `IUnknown` vrátit rozhraní, které může být dotazováno pro rozhraní [IDebugDocumentText2.](../../../extensibility/debugger/reference/idebugdocumenttext2.md) Podrobnosti najdete v části Poznámky.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby. Vrátí, `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` pokud neexistuje žádné rozšířené informace k načtení.

## <a name="remarks"></a>Poznámky
 Tato metoda existuje pro účely načítání informací, které se nehodí k načtení voláním metody [GetPropertyInfo.](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)

 Následující identifikátory GUID jsou obvykle rozpoznány touto metodou (hodnoty GUID jsou určeny pro C#, protože název není k dispozici v žádném sestavení). Pro interní použití lze vytvořit další identifikátory GUID.

|Name (Název)|GUID|Popis|
|----------|----------|-----------------|
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|Vrátí `IUnknown` rozhraní do dokumentu. Rozhraní [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) lze obvykle získat z `IUnknown` tohoto rozhraní.|
|guidCodeContext|{e2fc65e-56ce-11d1-b528-00ax004a8797}|Vrátí `IUnknown` rozhraní do kontextu dokumentu. Rozhraní [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) lze obvykle získat z `IUnknown` tohoto rozhraní.|
|podpora guidCustomViewer|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Vrátí řetězec obsahující CLSID vlastního prohlížeče, obvykle implementovaný vyhodnocením výrazu.|
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|Vrátí 32bitové číslo představující požadované číslo patice, pokud tato vlastnost představuje místní adresu spravovaného kódu.|
|guidExtendedInfoPodpis|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Vrátí řetězec obsahující podpis proměnné přidružené k objektu vlastnosti.|

## <a name="see-also"></a>Viz také
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
