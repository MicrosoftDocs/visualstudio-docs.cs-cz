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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: eaf58f312afd379fb1f16d208c323777ec725231
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860604"
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
