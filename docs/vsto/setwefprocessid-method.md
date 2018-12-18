---
title: Setwefprocessid – metoda
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b426237816bfee53e7c3e50c19e29168b27e16e1
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693429"
---
# <a name="setwefprocessid-method"></a>Setwefprocessid – metoda
  Poskytuje identifikátor procesu, který se spustí Web rozšíření Framework (WEF) obsah.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|*dwProcessId*|Identifikátor procesu, který se použije ke spuštění WEF obsah.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Hodnota HRESULT, která určuje, zda metoda byla úspěšně dokončena.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda musí být volána po vytvoření procesu WEF obsahu, ale před spuštěním jakékoli WEF obsah.  
  
 Pokud chcete připojit ladicí program k obsahu proces WEF vývojového prostředí, prostředí musí provést tuto operaci v vaší implementace této metody.  
  
  