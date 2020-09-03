---
title: 'IDebugProgramProvider2:: GetProviderProcessData | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
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
pro Kombinace příznaků z výčtu [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) . Pro toto volání jsou typické následující příznaky:

|Příznak|Popis|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|Volající je spuštěný na vzdáleném počítači.|
|`PFLAG_DEBUGGEE`|Právě probíhá ladění volajícího (pro každý uzel se vrátí další informace o zařazování).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Volající byl připojen k, ale nespustí ho ladicí program.|
|`PFLAG_GET_PROGRAM_NODES`|Volající žádá o seznam uzlů programu, které se mají vrátit.|

`pPort`\
pro Port, na kterém je spuštěn volající proces.

`processId`\
pro Struktura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) drží ID procesu, který obsahuje daný program.

`EngineFilter`\
pro Pole identifikátorů GUID pro ladicí moduly přiřazené k ladění tohoto procesu (budou použity k filtrování programů, které jsou skutečně vráceny na základě toho, co dodaných modulů podporuje; Pokud nejsou zadány žádné moduly, budou vráceny všechny programy).

`pProcess`\
mimo [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) struktura, která je vyplněna požadovanými informacemi.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda je obvykle volána procesem, aby získala seznam programů spuštěných v tomto procesu. Vrácené informace jsou seznam objektů [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) .

## <a name="see-also"></a>Viz také
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
