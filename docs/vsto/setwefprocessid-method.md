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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 523279d70215af90ea070ea8272a5221d9947582
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524324"
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
