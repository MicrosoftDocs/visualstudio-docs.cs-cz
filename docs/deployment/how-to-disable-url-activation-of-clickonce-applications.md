---
title: Zakázat aktivaci adresy URL aplikací ClickOnce
description: Zjistěte, jak zakázat automatické spouštění při instalaci pro aplikaci ClickOnce, pokud chcete, aby uživatelé spustili aplikaci z nabídky Start.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1e721199716abc47e89dc9fd2c7c510926853439
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900696"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Postupy: zákaz aktivace adresy URL aplikací ClickOnce

Obvykle se [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace automaticky spustí hned po instalaci z webového serveru. Z bezpečnostních důvodů se můžete rozhodnout toto chování zakázat a uživatelům sdělit, aby aplikaci spustili z nabídky **Start** . Následující postup popisuje, jak zakázat aktivaci adresy URL.

Tato technika se dá použít jenom pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace nainstalované v počítači uživatele z webového serveru. Nedá se použít jenom pro online aplikace, které se dají spustit jenom pomocí jejich adresy URL. Další informace o rozdílu mezi online a nainstalovanými aplikacemi najdete v tématu [volba strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

Tento postup používá MageUI.exe nástroje Windows Software Development Kit (SDK). Další informace o tomto nástroji najdete v tématu [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Tento postup můžete provést také pomocí sady Visual Studio.

## <a name="procedure"></a>Postup

### <a name="to-disable-url-activation-for-your-application"></a>Zakázání aktivace adresy URL pro vaši aplikaci

1. Otevřete manifest nasazení v MageUI.exe. Pokud jste ho ještě nevytvořili, postupujte podle kroků v [návodu: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

2. Vyberte kartu **Možnosti nasazení** .

3. Zrušte zaškrtnutí políčka **automaticky spouštět aplikaci po instalaci** .

4. Uložte manifest a podepište ho.

## <a name="see-also"></a>Viz také

- [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)