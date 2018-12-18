---
title: Ladění ovládacího prvku ActiveX vázaného na Data | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data-bound controls, ActiveX
- ActiveX controls, debugging
- controls [Visual Studio], ActiveX
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 310fb717be7b79f0de6fe01203c862736555999c
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44278280"
---
# <a name="debugging-a-data-bound-activex-control"></a>Ladění ovládacího prvku ActiveX vázaného na data
Pokud vyvíjíte ovládacího prvku ActiveX, který bude vázán k ovládacímu prvku zdroje dat, můžete vytvořit svou vlastní aplikaci typu kontejner a použít tento kontejner Chcete-li ladit ovládací prvek ActiveX.  
  
 Můžete například vytvoření aplikace založené na dialogu MFC a umístit ovládací prvek vázaný na data a ovládací prvek zdroje dat v dialogovém okně. Tato aplikace knihovny MFC můžete použít pro testování za běhu a jako kontejner spustitelný pro ladění vašeho ovládacího prvku ActiveX vázaného na data.  
  
## <a name="using-the-test-container"></a>Pomocí testovacího kontejneru  
 Pokud chcete kontejner, který můžete snadno upravit pro podporu různých rozhraní buď ovládacího prvku nebo kontejneru, použijte kontejner testu ActiveX jako spustitelný soubor pro relaci ladění. V kontejneru testů ActiveX, klikněte na tlačítko **možnosti** z **kontejneru** nabídka umožňující různá rozhraní. Další informace najdete v tématu [testování vlastností a událostí pomocí testovacího kontejneru](/cpp/mfc/testing-properties-and-events-with-test-container).  
  
 Pokud je potřeba při ladění s vnořením do kontejneru kódu, použijte ladicí verze vašeho kontejneru nebo použijte ladicí verze v kontejneru testů ActiveX. Další informace najdete v tématu [lze kontejner TSTCON vzorku: kontejner testů ovládacích prvků ActiveX](https://msdn.microsoft.com/library/72fa40ef-27d3-400c-813f-10b03236e600).  
  
## <a name="see-also"></a>Viz také  
 [COM a ActiveX ladění](../debugger/com-and-activex-debugging.md)   
 [ActiveX – ovládací prvky](/cpp/mfc/activex-controls)