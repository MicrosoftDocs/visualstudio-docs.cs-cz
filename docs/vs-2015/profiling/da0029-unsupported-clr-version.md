---
title: 'DA0029: Nepodporovaná verze CLR | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51195b14be7bffe682f4ac8588e38c6f5bd56e58
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762532"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: Nepodporovaná verze CLR
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id pravidla | DA0029 |  
| Kategorie | Použití nástroje pro profilaci |  
| Metoda profilace | Profilace z příkazového řádku |  
| Zpráva | Během shromažďování byla zjištěna nepodporovaná verze CLR. Spravované symboly nemůže vyřešit správně. |  
| Typ pravidla | Informace o. |  
  
## <a name="cause"></a>příčina  
 Pokoušíte se profil aplikace, která se používá [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)] , která není podporována nástrojů pro profilaci.  
  
## <a name="rule-description"></a>Popis pravidla  
 K tomuto upozornění dochází, protože nástrojů pro profilaci, nebude možné vyřešit symboly pro spravovaný kód spuštěný v aplikaci. Nástroje pro profilaci nemůže vyřešit symboly spravovaného kódu pro aplikace, které jsou spuštěny [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)].  
  
## <a name="how-to-fix-violations"></a>Jak vyřešit porušení  
 Žádné



