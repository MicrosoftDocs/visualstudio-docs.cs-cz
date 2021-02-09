---
title: Přizpůsobení výchozí webové stránky pro aplikaci ClickOnce
description: Přečtěte si o webové stránce vygenerované při publikování aplikace ClickOnce na webu, která obsahuje název aplikace a další informace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish.htm Web page
- ClickOnce deployment default Web page
- deploying applications [ClickOnce], publishing
- publishing, ClickOnce
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0377bdc5fa38c814bb5cd6ff02d12dcec117266d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900792"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Postupy: přizpůsobení výchozí webové stránky pro aplikaci ClickOnce
Při publikování aplikace ClickOnce na web je automaticky generována a publikována webová stránka společně s aplikací. Výchozí stránka obsahuje název aplikace a odkazy na instalaci aplikace, instalaci požadovaných součástí nebo přístup k nápovědě na webu MSDN.

> [!NOTE]
> Skutečné odkazy zobrazené na stránce závisí na počítači, na kterém je stránka zobrazována, a na požadavcích, které máte, včetně.

 Výchozí název webové stránky je *Publish.htm*; název můžete změnit v **Návrháři projektu**. Další informace naleznete v tématu [How to: určení stránky publikování pro aplikaci ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).

 Webová stránka *Publish.htm* je publikována pouze v případě, že je zjištěna novější verze.

> [!NOTE]
> Změny provedené v nastavení **publikování** nebudou mít vliv na stránku *Publish.htm* s jednou výjimkou: Pokud po počátečním publikování přidáte nebo odeberete předpoklady, seznam požadovaných součástí už nebude přesný. Aby se změny projevily, budete muset upravit text pro odkaz na požadované součásti.

### <a name="to-customize-the-publish-web-page"></a>Přizpůsobení webové stránky publikovat

1. Publikujte aplikaci ClickOnce na umístění na webu. Další informace naleznete v tématu [How to: Publish a aplikace ClickOnce using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

2. Na webovém serveru otevřete *Publish.htm* soubor ve Visual Web designeru nebo v jiném editoru HTML.

3. Stránku upravte podle potřeby a uložte ji.

4. Nepovinný parametr. Chcete-li aplikaci Visual Studio zabránit v přepsání přizpůsobené webové stránky publikování, zrušte možnost **automaticky generovat webovou stránku nasazení po každém publikování** v dialogovém okně **Možnosti publikování** .

## <a name="see-also"></a>Viz také
- [Zabezpečení a nasazení ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Postupy: Instalace předpokladů s aplikací ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Postupy: určení stránky publikování pro aplikaci ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)