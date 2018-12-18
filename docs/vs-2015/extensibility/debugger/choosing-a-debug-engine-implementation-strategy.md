---
title: Výběr strategie implementace modulu ladění | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9d2f4d4f907dcabb2aff5457abbbe215507d7601
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734629"
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>Výběr strategie implementace ladicího stroje
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Určení strategie implementace ladicí stroj (DE) pomocí architektury za běhu. Ladicí stroj mohou být vytvořeny vnitroprocesové programu bude ladění, v rámci procesu Visual Studio relaci ladění správci, nebo na více instancí procesu do obou z nich. Následující pokyny využít k výběru mezi tyto tři strategie.  
  
## <a name="guidelines"></a>Pokyny  
 I když je možné pro Německo mimo proces SDM i program k ladění, obvykle neexistuje žádný důvod k tomu. Volání přes hranice procesu jsou relativně pomalé.  
  
 Ladění moduly jsou už k dispozici pro prostředí Win32 nativní za běhu a prostředí common language runtime. Pokud je třeba nahradit DE pro některý z těchto prostředí, je nutné vytvořit s SDM DE v rámci procesu.  
  
 V opačném případě můžete zvolit vytváření DE v rámci procesu SDM nebo v rámci procesu ladění programu. Je důležité vzít v úvahu, jestli vyhodnocovač výrazů DE potřebuje časté přístup k úložišti symbolů programu a určuje, zda úložiště symbolů je možné načíst do paměti pro rychlý přístup. Zvažte také následující:  
  
-   Pokud nejsou k dispozici mnoho volání mezi vyhodnocovací filtr výrazů a úložiště symbolů nebo úložiště symbolů lze načíst do paměti SDM, vytvořte DE v rámci procesu SDM. Identifikátor CLSID ladicí stroj musí vrátit SDM při připojování vašeho programu. K vytvoření instance v procesu je DE SDM používá tento identifikátor CLSID.  
  
-   Pokud DE musí volat program pro přístup k úložišti symbolů, vytvořte program DE v rámci procesu. V takovém případě program vytvoří instance DE.  
  
## <a name="see-also"></a>Viz také  
 [Rozšiřitelnost programu Visual Studio Debugger](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

