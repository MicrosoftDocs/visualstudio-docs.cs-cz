---
title: Ladění ovládacího prvku ActiveX vázaného na Data | Dokumentace Microsoftu
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
- data-bound controls, ActiveX
- ActiveX controls, debugging
- controls [Visual Studio], ActiveX
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ae8863b8622987c0676646f45b5659945971c464
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768864"
---
# <a name="debugging-a-data-bound-activex-control"></a>Ladění ovládacího prvku ActiveX vázaného na data
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud vyvíjíte ovládacího prvku ActiveX, který bude vázán k ovládacímu prvku zdroje dat, můžete vytvořit svou vlastní aplikaci typu kontejner a použít tento kontejner Chcete-li ladit ovládací prvek ActiveX.  
  
 Můžete například vytvoření aplikace založené na dialogu MFC a umístit ovládací prvek vázaný na data a ovládací prvek zdroje dat v dialogovém okně. Tato aplikace knihovny MFC můžete použít pro testování za běhu a jako kontejner spustitelný pro ladění vašeho ovládacího prvku ActiveX vázaného na data.  
  
## <a name="using-the-test-container"></a>Pomocí testovacího kontejneru  
 Pokud chcete kontejner, který můžete snadno upravit pro podporu různých rozhraní buď ovládacího prvku nebo kontejneru, použijte kontejner testu ActiveX jako spustitelný soubor pro relaci ladění. V kontejneru testů ActiveX, klikněte na tlačítko **možnosti** z **kontejneru** nabídka umožňující různá rozhraní. Další informace najdete v tématu [testování vlastností a událostí pomocí testovacího kontejneru](http://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917).  
  
 Pokud je potřeba při ladění s vnořením do kontejneru kódu, použijte ladicí verze vašeho kontejneru nebo použijte ladicí verze v kontejneru testů ActiveX. Další informace najdete v tématu [lze kontejner TSTCON vzorku: kontejner testů ovládacích prvků ActiveX](http://msdn.microsoft.com/en-us/72fa40ef-27d3-400c-813f-10b03236e600).  
  
## <a name="see-also"></a>Viz také  
 [COM a ActiveX ladění](../debugger/com-and-activex-debugging.md)   
 [ActiveX – ovládací prvky](http://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)



