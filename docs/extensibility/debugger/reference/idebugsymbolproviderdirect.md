---
description: Představuje poskytovatele symbolu, který má přímý přístup k rozhraním metadat a základních symbolů.
title: IDebugSymbolProviderDirect | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0d60af5be925341e5421badb4c3e6e3dae97903b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149311"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
Představuje poskytovatele symbolu, který má přímý přístup k rozhraním metadat a základních symbolů.

## <a name="syntax"></a>Syntax

```
IDebugSymbolProviderDirect: IUnknown
```

## <a name="methods"></a>Metody
 Toto rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Načte identifikátor domény aplikace, který je dán adresou pro ladění.|
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Načte informace o modulech ve skupině symbolů.|
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Načte informace o skupině symbolů, které je poskytovatel symbolů členem.|
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Načte informace o importu metadat.|
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Načte informace o metodě na zadané adrese pro ladění.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Načte čtečku symbolů pro nespravovaný kód.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní lze použít místo většiny ostatních rozhraní poskytovatele symbolů. Poskytuje přímý přístup k metadatům a `CorSym` rozhraním.

## <a name="requirements"></a>Požadavky
 Záhlaví: SH. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
