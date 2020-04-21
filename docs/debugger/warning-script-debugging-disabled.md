---
title: 'Upozornění: Ladění skriptů zakázáno | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.scriptdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 15de1a1e516cb3d84c24428ef04dd87baedaed9e
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81648507"
---
# <a name="warning-script-debugging-disabled"></a>Upozornění: Ladění skriptů zakázáno
Ladění skriptů je v aplikaci Internet Explorer aktuálně zakázáno.

 K tomuto upozornění dochází při pokusu o ladění skriptu bez povolení ladění skriptu v aplikaci Internet Explorer. Z bezpečnostních důvodů aplikace Internet Explorer ve výchozím nastavení zakáže ladění skriptů.

### <a name="to-enable-script-debugging-in-internet-explorer"></a>Povolení ladění skriptů v aplikaci Internet Explorer

1. V nabídce **Nástroje** aplikace Internet Explorer zvolte **Možnosti Internetu**.

2. V dialogu **Možnosti Internetu** klikněte na kartu **Upřesnit** .

3. Na kartě **Upřesnit** se podívejte do pole **Nastavení** V kategorii **Procházení.**

4. Zrušte **zaškrtnutí položky Disable Script Debugging (Internet Explorer).**

5. Klikněte na tlačítko **OK**.

6. Ukončete a restartujte aplikaci Internet Explorer.

     Nové nastavení bude nyní v platnosti.

## <a name="see-also"></a>Viz také
- [Postup: Připojení ke skriptu](attach-to-running-processes-with-the-visual-studio-debugger.md)