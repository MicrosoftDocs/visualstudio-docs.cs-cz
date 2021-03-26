---
description: Načte uzel programu pro určitý program.
title: 'IDebugProgramProvider2:: GetProviderProgramNode | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 07e7184c189d501b2fcb604590eeb121bae8ccdc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065278"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
Načte uzel programu pro určitý program.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProviderProgramNode(
   PROVIDER_FLAGS       Flags,
   IDebugDefaultPort2*  pPort,
   AD_PROCESS_ID        processId,
   REFGUID              guidEngine,
   UINT64               programId,
   IDebugProgramNode2** ppProgramNode
);
```

```csharp
int GetProviderProgramNode(
   enum_PROVIDER_FLAGS    Flags,
   IDebugDefaultPort2     pPort,
   AD_PROCESS_ID          ProcessId,
   ref Guid               guidEngine,
   ulong                  programId,
   out IDebugProgramNode2 ppProgramNode
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

`pPort`\
pro Port, na kterém je spuštěn volající proces.

`processId`\
pro Struktura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) drží ID procesu, který obsahuje daný program.

`guidEngine`\
pro Identifikátor GUID ladicího stroje, ke kterému je program připojen (pokud existuje)

`programId`\
pro ID programu, pro který se má získat uzel programu

`ppProgramNode`\
mimo Objekt [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , který představuje požadovaný uzel programu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
