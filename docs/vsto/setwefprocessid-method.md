---
title: Metoda Setwefprocessid –
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
ms.openlocfilehash: 13a6748e2e3b66f581a3c72c1f847e0329189e64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537329"
---
# <a name="setwefprocessid-method"></a>Metoda Setwefprocessid –
  Poskytuje identifikátor procesu, který spustí obsah architektury Web Extensions (WEF).

## <a name="syntax"></a>Syntaxe

```csharp
HRESULT SetWefProcessId(
    [in] DWORD dwProcessId
);
```

#### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*dwProcessId*|Identifikátor procesu, který se použije ke spuštění obsahu WEF.|

## <a name="return-value"></a>Vrácená hodnota
 Hodnota HRESULT, která označuje, zda byla metoda úspěšně dokončena.

## <a name="remarks"></a>Poznámky
 Tato metoda musí být volána po vytvoření procesu obsahu WEF, ale před spuštěním jakéhokoli WEF obsahu.

 Pokud chcete, aby vývojové prostředí připojilo ladicí program k procesu obsahu WEF, prostředí musí tuto operaci provést při implementaci této metody.
