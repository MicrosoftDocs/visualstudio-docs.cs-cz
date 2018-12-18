---
title: Hlediska zabezpečení Vizualizéru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- visualizers, security
- security [Visual Studio], visualizers
ms.assetid: cdd86bd5-b729-409b-a7c6-374efa091eb1
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b25c9a183a843130861818f8a80948a68a8b1ed5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800624"
---
# <a name="visualizer-security-considerations"></a>Hlediska zabezpečení vizualizéru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zápis Vizualizéru zahrnuje možné bezpečnostní hrozby. Žádné známé před zneužitím v současné době neexistuje těchto potenciálních hrozeb, ale by měl být vědomi a přijmout vhodná bezpečnostní opatření, podle postupu popsaného tady, pro ochranu proti zneužití budoucí vývojáři.  
  
 Ladicí program vizualizéry vyžadují, aby větší oprávnění než je povoleno hodnotou aplikace s částečnou důvěryhodností. Vizualizéry nenačte, když se zastaví v kódu s částečným vztahem důvěryhodnosti. Chcete-li ladit pomocí vizualizéru, musíte spustit kód s úplným vztahem důvěryhodnosti.  
  
## <a name="possible-malicious-debuggee-component"></a>Je to možné škodlivé součásti laděného procesu  
 Vizualizéry skládají z nejméně dvou tříd: na straně ladicího programu a druhý na straně laděného procesu. Vizualizéry jsou často nasazené v samostatné sestavení umístit do speciální adresáře, ale mohou být načteny z laděného procesu. Pokud k tomu dojde, ladicí program přijímá kódu mimo laděný proces a běží uvnitř ladicího programu s úplným vztahem důvěryhodnosti.  
  
 Spuštění kódu na straně laděného procesu s úplným vztahem důvěryhodnosti je problematické, pokud laděný proces není plně důvěryhodné. Pokud vizualizéru se pokusí načíst sestavení s částečnou nedůvěrou z laděného procesu do ladicího programu, Visual Studio se ukončí vizualizér.  
  
 Nicméně stále existuje menší ohrožení zabezpečení. Na straně laděného procesu můžete přidružit souběžného ladicí program, který byl načten z jiného zdroje (ne laděného procesu). Na straně laděného procesu pak poznáte, která důvěryhodného straně ladicího programu k provádění akcí na jejím jménem. Pokud důvěryhodné ladicí program side třída zveřejňuje mechanismus "odstranit tento soubor", například laděného procesu částečným vztahem důvěryhodnosti mohl spustit tento mechanismus když uživatel vyvolá jeho vizualizér.  
  
 Ke zmírnění tohoto ohrožení zabezpečení, dávejte rozhraní vystavené vaše vizualizér.  
  
## <a name="see-also"></a>Viz také  
 [Architektura vizualizéru](../debugger/visualizer-architecture.md)   
 [Postupy: zápis Vizualizéru](../debugger/how-to-write-a-visualizer.md)   
 [Vytváření vlastních Vizualizérů](../debugger/create-custom-visualizers-of-data.md)   
 [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)



