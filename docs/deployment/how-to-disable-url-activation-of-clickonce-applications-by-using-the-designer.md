---
title: Zakázání aktivace adresy URL aplikací ClickOnce pomocí návrháře
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 818ab634d48fb666ecab5d89464ea017040bd250
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382481"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Postupy: zákaz aktivace adresy URL aplikací ClickOnce pomocí návrháře
Obvykle se [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace automaticky spustí hned po instalaci z webového serveru. Z bezpečnostních důvodů se můžete rozhodnout toto chování zakázat a uživatelům sdělit, aby aplikaci spustili z nabídky **Start** . Následující postup popisuje, jak zakázat aktivaci adresy URL.

 Tato technika se dá použít jenom pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace nainstalované v počítači uživatele z webového serveru. Nedá se použít jenom pro online aplikace, které se dají spustit jenom pomocí jejich adresy URL. Další informace o rozdílu mezi online a nainstalovanými aplikacemi najdete v tématu [volba strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

 Tato procedura používá [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Tuto úlohu můžete provést také pomocí [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] . Další informace najdete v tématu [Postup: zákaz aktivace adresy URL aplikací ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).

## <a name="procedure"></a>Postup

#### <a name="to-disable-url-activation-for-your-application"></a>Zakázání aktivace adresy URL pro vaši aplikaci

1. Klikněte pravým tlačítkem myši na název projektu v **Průzkumník řešení**a klikněte na **vlastnosti**.

2. Na stránce **vlastnosti** klikněte na kartu **publikovat** .

3. Klikněte na tlačítko **Možnosti**.

4. Klikněte na **manifesty**.

5. Zaškrtněte políčko označeno **blokem blokování aplikace, které se aktivuje prostřednictvím adresy URL**.

6. Nasaďte aplikaci.

## <a name="see-also"></a>Viz také
- [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)