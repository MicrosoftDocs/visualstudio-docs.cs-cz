---
title: IDebugProgramProvider2::GetProviderProcessData | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4e958900307f5f7915f58679709c88f80c2abfc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721850"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
Načte seznam spuštěných programů ze zadaného procesu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProviderProcessData(
   PROVIDER_FLAGS         Flags,
   IDebugDefaultPort2*    pPort,
   AD_PROCESS_ID          processId,
   CONST_GUID_ARRAY       EngineFilter,
   PROVIDER_PROCESS_DATA* pProcess
);
```

```csharp
int GetProviderProcessData(
   enum_PROVIDER_FLAGS     Flags,
   IDebugDefaultPort2      pPort,
   AD_PROCESS_ID           ProcessId,
   CONST_GUID_ARRAY        EngineFilter,
   PROVIDER_PROCESS_DATA[] pProcess
);
```

## <a name="parameters"></a>Parametry
`Flags`\
[v] Kombinace příznaků z [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) výčtu. Pro toto volání jsou typické následující příznaky:

|Příznak|Popis|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|Volající je spuštěn na vzdáleném počítači.|
|`PFLAG_DEBUGGEE`|Volající je aktuálně laděno (další informace o zařazování budou vráceny pro každý uzel).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Volající byl připojen k ladicímu programu, ale nebyl spuštěn.|
|`PFLAG_GET_PROGRAM_NODES`|Volající žádá o seznam programových uzlů, které mají být vráceny.|

`pPort`\
[v] Port, na který je spuštěn volající proces.

`processId`\
[v] [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struktury, která obsahuje ID procesu, který obsahuje daný program.

`EngineFilter`\
[v] Pole identifikátorů GUID pro ladicí moduly přiřazené k ladění tohoto procesu (ty budou použity k filtrování programů, které jsou skutečně vráceny na základě toho, co podporují dodávané motory; pokud nejsou zadány žádné motory, budou vráceny všechny programy).

`pProcess`\
[out] [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) struktura, která je vyplněna požadovanými informacemi.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda je obvykle volána procesem k získání seznamu programů spuštěných v tomto procesu. Vrácené informace jsou seznamem objektů [IDebugProgramNode2.](../../../extensibility/debugger/reference/idebugprogramnode2.md)

## <a name="see-also"></a>Viz také
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
