---
title: 'Postupy: přizpůsobení výchozí webové stránky pro aplikaci ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4ec63fe5ae4b99252321b86b44066c46842a0851
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64779684"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Postupy: Úprava výchozí webové stránky pro aplikaci ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při publikování aplikace ClickOnce na web je automaticky generována a publikována webová stránka společně s aplikací. Výchozí stránka obsahuje název aplikace a odkazy na instalaci aplikace, instalaci požadovaných součástí nebo přístup k nápovědě na webu MSDN.  
  
> [!NOTE]
> Skutečné odkazy zobrazené na stránce závisí na počítači, na kterém je stránka zobrazována, a na požadavcích, které máte, včetně.  
  
 Výchozí název webové stránky je Publish.htm; název můžete změnit v **Návrháři projektu**. Další informace naleznete v tématu [How to: určení stránky publikování pro aplikaci ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).  
  
 Webová stránka Publish.htm je publikována pouze v případě, že je zjištěna novější verze.  
  
> [!NOTE]
> Změny provedené v nastavení **publikování** nebudou mít vliv na stránku Publish.htm s jednou výjimkou: Pokud po počátečním publikování přidáte nebo odeberete předpoklady, seznam požadovaných součástí už nebude přesný. Aby se změny projevily, budete muset upravit text pro odkaz na požadované součásti.  
  
### <a name="to-customize-the-publish-web-page"></a>Přizpůsobení webové stránky publikovat  
  
1. Publikujte aplikaci ClickOnce na umístění na webu. Další informace naleznete v tématu [How to: Publish a aplikace ClickOnce using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
2. Na webovém serveru otevřete Publish.htm soubor ve Visual Web designeru nebo v jiném editoru HTML.  
  
3. Stránku upravte podle potřeby a uložte ji.  
  
4. Nepovinný parametr. Chcete-li aplikaci Visual Studio zabránit v přepsání přizpůsobené webové stránky publikování, zrušte možnost **automaticky generovat webovou stránku nasazení po každém publikování** v dialogovém okně Možnosti publikování.  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)   
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Postupy: Instalace předpokladů s aplikací ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Postupy: Určení stránky publikování pro aplikaci ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)
