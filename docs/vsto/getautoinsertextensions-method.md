---
description: Načte informace o aplikacích pro Office, které se mají automaticky vkládat během ladění.
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
ms.openlocfilehash: c4a49942f50a79db604d2363cf2d85762c5ddce5
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223430"
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
