---
title: GetValidCompatibleFramework – – funkce
description: Přečtěte si, jak rozhraní GetValidCompatibleFramework – API podporuje infrastrukturu Office a není určené pro použití přímo v kódu.
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
ms.openlocfilehash: b089f954c59219461c8e267ee6e88e47015fc794
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860617"
---
# <a name="getvalidcompatibleframework-function"></a>GetValidCompatibleFramework – – funkce
  Toto rozhraní API podporuje infrastrukturu Office a není určené pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```csharp
HRESULT WINAPI GetValidCompatibleFramework(
    LPCWSTR lpwszCompatibleFrameworksXML,
    BSTR* pbstrValidFrameworkTag
);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*lpwszCompatibleFrameworksXML*|Nepoužívejte.|
|*pbstrValidFrameworkTag*|Nepoužívejte.|

## <a name="return-value"></a>Vrácená hodnota
 Pokud je funkce úspěšná, vrátí **S_OK**. Pokud funkce dojde k chybě, vrátí kód chyby.
