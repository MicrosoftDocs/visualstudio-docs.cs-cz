---
title: Metoda Setwefprocessid –
description: Přečtěte si, jak metoda Setwefprocessid – poskytuje identifikátor procesu, který bude spouštět obsah rozhraní Web Extensions (WEF).
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
ms.openlocfilehash: 9c3d745f14185d46dce08d46b8c56391b108627d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882405"
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
