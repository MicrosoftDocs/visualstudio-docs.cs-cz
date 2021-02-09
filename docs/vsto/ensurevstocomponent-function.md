---
title: EnsureVSTOComponent – – funkce
description: Přečtěte si, jak rozhraní EnsureVSTOComponent – API podporuje infrastrukturu Office a není určené pro použití přímo v kódu.
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
ms.openlocfilehash: 17f52a469d93a843ef776c125e15a37db22277e8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910475"
---
# <a name="ensurevstocomponent-function"></a>EnsureVSTOComponent – – funkce
  Toto rozhraní API podporuje infrastrukturu Office a není určené pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```csharp
HRESULT EnsureVSTOComponent(
    IVSTProject *pProject
);
```

#### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pProject*|Nepoužívejte.|

## <a name="return-value"></a>Vrácená hodnota
 Pokud je funkce úspěšná, vrátí **S_OK**. Pokud funkce dojde k chybě, vrátí kód chyby.
