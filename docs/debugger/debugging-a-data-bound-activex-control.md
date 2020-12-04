---
title: Ladění ovládacího prvku Data-Bound ActiveX | Microsoft Docs
description: Naučte se ladit ovládací prvek ActiveX vázaný na ovládací prvek zdroje dat vytvořením aplikace typu kontejner pro ladění.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: a999014309c4545067967b77d1b91794e4bd3c99
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560717"
---
# <a name="debugging-a-data-bound-activex-control"></a>Ladění ovládacího prvku ActiveX vázaného na data
Pokud vyvíjíte ovládací prvek ActiveX, který bude svázán s ovládacím prvkem zdroje dat, můžete vytvořit vlastní aplikaci typu kontejner a použít tento kontejner k ladění ovládacího prvku ActiveX.

 Můžete například vytvořit aplikaci MFC založenou na dialogovém okně a umístit ovládací prvek vázaný na data a ovládací prvek zdroje dat do dialogového okna. Tuto aplikaci knihovny MFC lze použít pro testování za běhu a jako spustitelný soubor kontejneru pro ladění ovládacího prvku ActiveX vázaného na data.

## <a name="using-the-test-container"></a>Použití kontejneru testů
 Pokud chcete kontejner, který lze snadno upravit pro podporu různých rozhraní v ovládacím prvku nebo kontejneru, použijte jako spustitelný soubor pro ladicí relaci kontejner testu ActiveX. V kontejneru testu ActiveX klikněte na **Možnosti** v nabídce **kontejner** a povolte různá rozhraní. Další informace naleznete v tématu [Testování vlastností a událostí pomocí kontejneru testů](/cpp/mfc/testing-properties-and-events-with-test-container).

 Pokud potřebujete Krokovat s kódem kontejneru při ladění, použijte ladicí verzi vašeho kontejneru nebo použijte ladicí verzi kontejneru testu ActiveX. Další informace najdete v tématu [Ukázka TSTCON: kontejner testu ovládacího prvku ActiveX](/previous-versions/f9adb5t5(v=vs.100)).

## <a name="see-also"></a>Viz také:
- [Ladění modelu COM a ActiveX](../debugger/com-and-activex-debugging.md)
- [Ovládací prvky ActiveX](/cpp/mfc/activex-controls)