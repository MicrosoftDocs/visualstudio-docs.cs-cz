---
title: EnsureVSTOComponent – – funkce
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
ms.openlocfilehash: cf55fc6669edd33d1b8896ee85f33ab2c04e844f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543582"
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
