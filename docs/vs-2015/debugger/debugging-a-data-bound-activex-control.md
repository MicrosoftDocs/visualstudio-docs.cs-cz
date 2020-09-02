---
title: Ladění ovládacího prvku ActiveX vázaného na data | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 6945d1ccf72385b4d2fbe76736668e84b804e446
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686752"
---
# <a name="debugging-a-data-bound-activex-control"></a>Ladění ovládacího prvku ActiveX vázaného na data
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud vyvíjíte ovládací prvek ActiveX, který bude svázán s ovládacím prvkem zdroje dat, můžete vytvořit vlastní aplikaci typu kontejner a použít tento kontejner k ladění ovládacího prvku ActiveX.  
  
 Můžete například vytvořit aplikaci MFC založenou na dialogovém okně a umístit ovládací prvek vázaný na data a ovládací prvek zdroje dat do dialogového okna. Tuto aplikaci knihovny MFC lze použít pro testování za běhu a jako spustitelný soubor kontejneru pro ladění ovládacího prvku ActiveX vázaného na data.  
  
## <a name="using-the-test-container"></a>Použití kontejneru testů  
 Pokud chcete kontejner, který lze snadno upravit pro podporu různých rozhraní v ovládacím prvku nebo kontejneru, použijte jako spustitelný soubor pro ladicí relaci kontejner testu ActiveX. V kontejneru testu ActiveX klikněte na **Možnosti** v nabídce **kontejner** a povolte různá rozhraní. Další informace naleznete v tématu [Testování vlastností a událostí pomocí kontejneru testů](https://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917).  
  
 Pokud potřebujete Krokovat s kódem kontejneru při ladění, použijte ladicí verzi vašeho kontejneru nebo použijte ladicí verzi kontejneru testu ActiveX. Další informace najdete v tématu [Ukázka TSTCON: kontejner testu ovládacího prvku ActiveX](https://msdn.microsoft.com/72fa40ef-27d3-400c-813f-10b03236e600).  
  
## <a name="see-also"></a>Viz také  
 [Ladění modelu COM a ActiveX](../debugger/com-and-activex-debugging.md)   
 [Ovládací prvky ActiveX](https://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)
