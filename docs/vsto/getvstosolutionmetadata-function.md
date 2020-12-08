---
title: GetVstoSolutionMetadata – – funkce
description: Přečtěte si, jak rozhraní GetVstoSolutionMetadata – API podporuje infrastrukturu Office a není určené pro použití přímo v kódu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 205bde9352e2a037b4a08108d8cfce3460034e66
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845034"
---
# <a name="getvstosolutionmetadata-function"></a>GetVstoSolutionMetadata – – funkce
  Toto rozhraní API podporuje infrastrukturu Office a není určené pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```csharp
HRESULT WINAPI GetVstoSolutionMetadata(
    LPCWSTR lpwszSolutionMetadataKey,
    ISolutionMetadata** ppSolutionInfo
);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*lpwszSolutionMetadataKey*|Nepoužívejte.|
|*ppSolutionInfo*|Nepoužívejte.|

## <a name="return-value"></a>Vrácená hodnota
 Pokud je funkce úspěšná, vrátí **S_OK**. Pokud funkce dojde k chybě, vrátí kód chyby.
