---
title: CaptureCurrentFrame | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 41169494424310427e5a8ae6a0af533bdf4be834
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471230"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Zaznamená zbytek aktuální rámec grafiky souboru protokolu.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud aktuálně probíhá jiná zachycení – například zachycení, která byla spuštěna `BeginCapture` funkce – tento snímek je dokončena a zaznamenány do protokolu grafiky jako odlišné rámce. Okamžitě diagnostiky grafiky později, začne zaznamenávání zbytek aktuální rámce, který je taky zaznamená jako odlišné rámce. Aktuální snímek end je označena kvalifikátorem volání k dispozici.  
  
 Když Pokud chcete zachytit snímek, je nutné připravit aplikace k zaznamenání a zaznamenání grafických informací – tedy můžete musí mít volána [Init](init.md) prostřednictvím instance `VsgDbg` třídy před voláním `CaptureCurrentFrame`.  
  
## <a name="see-also"></a>Viz také  
 [Init –](init.md)   
 [BeginCapture](begincapture.md)