---
title: Metoda Getautoinsertextensions –
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
ms.openlocfilehash: 24fd5768a9eafa4a023aeabf21c862ea1a0d1891
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931523"
---
# <a name="getautoinsertextensions-method"></a>Metoda Getautoinsertextensions –
  Načte informace o aplikacích pro Office, které se mají automaticky vkládat během ladění.

 Tato metoda je vyhrazena pro budoucí použití.

## <a name="syntax"></a>Syntaxe

```csharp
HRESULT GetAutoInsertExtensions(
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames
);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*psaExtensionNames*|Názvy rozšíření aplikací pro Office.|

## <a name="return-value"></a>Vrácená hodnota
 Hodnota HRESULT, která označuje, zda byla metoda úspěšně dokončena.

## <a name="remarks"></a>Poznámky
 Každá aplikace pro Office, která se má vložit, se vrátí jako název rozšíření aplikace Office, který odpovídá hodnotě **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**. Hostitel musí vyhledat tyto hodnoty v registru a pak automaticky vkládat rozšíření.
