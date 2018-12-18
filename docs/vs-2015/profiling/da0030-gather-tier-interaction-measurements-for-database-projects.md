---
title: 'DA0030: Získat měření interakce vrstev pro databázové projekty | Dokumentace Microsoftu'
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
- vs.performance.DA0030
- vs.performance.rules.DA0030
- vs.performance.30
ms.assetid: 42b2f69d-0cfa-4854-82c4-589c3d8b4557
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16d6275074b3cae6b186fe9bb113e32c33e284af
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796750"
---
# <a name="da0030-gather-tier-interaction-measurements-for-database-projects"></a>DA0030: Získat Měření interakce vrstev pro databázové projekty
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id pravidla | DA0030 |  
| Kategorie | Použití nástroje pro profilaci |  
| Metoda profilace | Vzorkování |  
| Zpráva | Shromažďování měření interakce pro více vrstvé aplikace se vám pomůžou pochopit, způsobů využití databází a klíče dat přístup ke zpoždění. Zkuste profilaci aplikace znovu s povolenou možností profilace interakce vrstev. |  
| Typ pravidla | Informace |  
  
## <a name="cause"></a>příčina  
 Volání <xref:System.Data> podstatnou část dat profilování jsou metody a nebyly shromážděných dat interakce vrstev při spuštění profilace. Zvažte profilaci znovu a přidání dat interakce vrstev.  
  
## <a name="rule-description"></a>Popis pravidla  
 Toto pravidlo je vyvoláno, vždycky, když je funkce, které se nacházejí v oborech názvů System.Data, včetně významnou aktivitu <xref:System.Data.Linq> <xref:System.Data.Linq>.  
  
 Vícevrstvé aplikace pomocí vrstvy služeb pro své prezentaci a datové vrstvy. Často je datová vrstva samostatný proces běží systém správy databáze, jako je Microsoft Sql Server. Datová vrstva může být spuštěn i v samostatném počítači ze zbývajících částí aplikace. Vzorkování profily poskytují trochu přehled funkcí a služeb spuštěných na více instancí procesu nebo vzdáleně.  
  
 Nástroje pro profilování může shromažďovat informace o časování pro více vrstvé aplikace, které interagují s datové vrstvě Microsoft Sql Server, pomocí asynchronního volání služeb ADO.NET. Musíte explicitně povolit profilaci interakce vrstev. Není zapnutá ve výchozím nastavení.  
  
## <a name="how-to-fix-violations"></a>Jak vyřešit porušení  
 Toto pravidlo je pouze pro informaci a nemusí potřebovat nápravné opatření.  
  
 Informace o způsobu přidání dat interakce vrstev data profilace v integrovaném vývojovém prostředí sady Visual Studio najdete v tématu [shromažďování dat interakce vrstev](../profiling/collecting-tier-interaction-data.md). Informace o způsobu přidání dat interakce vrstev z příkazového řádku najdete v tématu [shromažďování dat interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md).



