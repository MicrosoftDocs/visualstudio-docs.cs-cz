---
title: 'Upozornění: ladění skriptů zakázáno | Microsoft Docs'
description: Při pokusu o ladění skriptu bez povolení ladění skriptu v aplikaci Internet Explorer dojde k upozornění "zakázáno ladění skriptů". Podívejte se na postup, jak ho povolit.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 052445b1dbb69c433220caf5764413e04f0909fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883997"
---
# <a name="warning-script-debugging-disabled"></a>Upozornění: Ladění skriptů zakázáno
Ladění skriptů je momentálně v Internet Exploreru zakázané.

 K tomuto upozornění dochází při pokusu o ladění skriptu bez povolení ladění skriptu v aplikaci Internet Explorer. Z bezpečnostních důvodů Internet Explorer ve výchozím nastavení zakáže ladění skriptu.

### <a name="to-enable-script-debugging-in-internet-explorer"></a>Povolení ladění skriptu v aplikaci Internet Explorer

1. V nabídce **nástroje** Internet Exploreru vyberte **Možnosti Internetu**.

2. V dialogu **Možnosti Internetu** klikněte na kartu **Upřesnit** .

3. Na kartě **Upřesnit** se podívejte do pole **Nastavení** , v kategorii **procházení** .

4. Zrušte zaškrtnutí políčka **Zakázat ladění skriptů (Internet Explorer)**.

5. Klikněte na **OK**.

6. Ukončete a znovu spusťte aplikaci Internet Explorer.

     Nové nastavení bude platit nyní.

## <a name="see-also"></a>Viz také
- [Postupy: připojení ke skriptu](attach-to-running-processes-with-the-visual-studio-debugger.md)