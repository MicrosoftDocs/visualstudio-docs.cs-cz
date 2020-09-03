---
title: Metoda Getautoinsertextensions –
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
ms.openlocfilehash: f5d88af6f24306b7b243359c9797a2cb7e7449bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543504"
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
 Každá aplikace pro Office, která se má vložit, se vrátí jako název rozšíření aplikace Office, který odpovídá hodnotě **HKEY_CURRENT_USER \software\microsoft\office\wef\developer**. Hostitel musí vyhledat tyto hodnoty v registru a pak automaticky vkládat rozšíření.
