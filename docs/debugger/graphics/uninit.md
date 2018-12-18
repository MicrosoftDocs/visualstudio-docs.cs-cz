---
title: UnInit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 56aa940d65934f7cc72f692f5bdf5e44854d276c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471450"
---
# <a name="uninit"></a>UnInit
Dokončí soubor protokolu grafiky, zavře se a uvolní prostředky, které jste použili při aplikaci se aktivně zaznamenání grafických informací.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
void UnInit();  
```  
  
## <a name="remarks"></a>Poznámky  
 `UnInit` je volána automaticky, když instance `VsgDbg` třída zničena. Pokud `VsgDbg` instance nebyla aktivně zaznamenání grafických informací, tato akce nemá vliv.  
  
 Po `UnInit` byla volána na instanci systému `VsgDbg` třídy, nové grafiky souboru protokolu lze vytvořit voláním `Init` a dokončené voláním `UnInit`. To můžete opakovat tolikrát, kolikrát chcete použít stejné `VsgDbg` instance vytvořit několik nezávislých grafiky soubory protokolu.  
  
## <a name="see-also"></a>Viz také  
 [Init](init.md)