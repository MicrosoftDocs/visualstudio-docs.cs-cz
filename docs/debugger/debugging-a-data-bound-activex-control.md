---
title: Ladění ovládacího prvku ActiveX vázaného na data | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 460277670d76ddcc1001ba2d6060107ea405601e
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350521"
---
# <a name="debugging-a-data-bound-activex-control"></a>Ladění ovládacího prvku ActiveX vázaného na data
Pokud vyvíjíte ovládací prvek ActiveX, který bude svázán s ovládacím prvkem zdroje dat, můžete vytvořit vlastní aplikaci typu kontejner a použít tento kontejner k ladění ovládacího prvku ActiveX.

 Můžete například vytvořit aplikaci MFC založenou na dialogovém okně a umístit ovládací prvek vázaný na data a ovládací prvek zdroje dat do dialogového okna. Tuto aplikaci knihovny MFC lze použít pro testování za běhu a jako spustitelný soubor kontejneru pro ladění ovládacího prvku ActiveX vázaného na data.

## <a name="using-the-test-container"></a>Použití kontejneru testů
 Pokud chcete kontejner, který lze snadno upravit pro podporu různých rozhraní v ovládacím prvku nebo kontejneru, použijte jako spustitelný soubor pro ladicí relaci kontejner testu ActiveX. V kontejneru testu ActiveX klikněte na **Možnosti** v nabídce **kontejner** a povolte různá rozhraní. Další informace naleznete v tématu [Testování vlastností a událostí pomocí kontejneru testů](/cpp/mfc/testing-properties-and-events-with-test-container).

 Pokud potřebujete Krokovat s kódem kontejneru při ladění, použijte ladicí verzi vašeho kontejneru nebo použijte ladicí verzi kontejneru testu ActiveX. Další informace najdete v tématu [Ukázka TSTCON: kontejner testu ovládacího prvku ActiveX](https://msdn.microsoft.com/library/72fa40ef-27d3-400c-813f-10b03236e600).

## <a name="see-also"></a>Viz také
- [Ladění modelů COM a prvků ActiveX](../debugger/com-and-activex-debugging.md)
- [ActiveX – ovládací prvky](/cpp/mfc/activex-controls)