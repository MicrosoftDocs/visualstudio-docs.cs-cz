---
description: Určuje umístění zadaného odkazu spravovaného sestavení.
title: 'IPropertyProxyEESide:: ResolveAssemblyRef | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
helpviewer_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
ms.assetid: 662ca0a6-dad0-4c00-a718-bb3bbc5bd9da
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 687ca5922cc59322c37b7b391a9b5f40d52c14ad
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225575"
---
# <a name="ipropertyproxyeesideresolveassemblyref"></a>IPropertyProxyEESide::ResolveAssemblyRef
Určuje umístění zadaného odkazu spravovaného sestavení.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ResolveAssemblyRef(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  assemLocation,
   ASSEMBLYLOCRESOLUTION* alr
);
```

```csharp
int ResolveAssemblyRef(
   ref string                     assemName,
   out IEEDataStorage             assemBytes,
   out IEEDataStorage             assemPdb,
   out string                     assemLocation,
   out enum_ASSEMBLYLOCRESOLUTION alr
);
```

## <a name="parameters"></a>Parametry
`assemName`\
pro Název sestavení, které chcete přeložit.

`assemBytes`\
mimo Vrátí objekt [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) obsahující bajty sestavení přidružené k odkazu.

`assemPdb`\
mimo Vrátí `IEEDataStorage` objekt obsahující data úložiště symbolů přidružená k tomuto odkazu.

`assemLocation`\
mimo Vrátí umístění cesty tohoto odkazu.

`alr`\
mimo Vrátí hodnotu z výčtu [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) , která označuje umístění sestavení tohoto odkazu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda není obvykle implementována pomocí vlastního vyhodnocovacího filtru výrazů.

## <a name="see-also"></a>Viz také
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
