---
title: 'DA0029: Nepodporovaná verze CLR | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: 532427618f476e1e187d8a1c88749810f9d157c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152645"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: Nepodporovaná verze CLR
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ID pravidla | DA0029 |  
| Kategorie | Využití Nástroje pro profilaci |  
| Metoda profilování | Profilace z příkazového řádku |  
| Zpráva | Během shromažďování byla zjištěna nepodporovaná verze CLR. Spravované symboly se nemusí správně přeložit. |  
| Typ pravidla | Informace. |  
  
## <a name="cause"></a>Příčina  
 Pokoušíte se profilovat aplikaci, která používá rozhraní [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)] , které není nástroje pro profilaci podporováno.  
  
## <a name="rule-description"></a>Popis pravidla  
 K tomuto upozornění dochází, protože nástroje pro profilaci nebudou moci přeložit symboly pro spravovaný kód spuštěný v aplikaci. Nástroje pro profilaci nemůžou přeložit spravované symboly kódu pro aplikace, na kterých běží [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)] .  
  
## <a name="how-to-fix-violations"></a>Jak vyřešit porušení  
 Žádné
