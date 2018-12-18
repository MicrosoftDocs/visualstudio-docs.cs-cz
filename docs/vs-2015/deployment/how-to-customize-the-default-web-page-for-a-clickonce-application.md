---
title: 'Postupy: Úprava výchozí webové stránky pro aplikaci ClickOnce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: b87019a824acada616865fd65cfd6aade8aa6ec9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49243422"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Postupy: Úprava výchozí webové stránky pro aplikaci ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při publikování aplikace ClickOnce k webu, je automaticky generována a spolu s aplikace publikována na webové stránce. Výchozí stránka obsahuje název aplikace a odkazy na instalaci aplikace, instalace požadovaných součástí nebo nápovědu na webu MSDN.  
  
> [!NOTE]
>  Skutečné odkazy, které se zobrazí na stránce jsou závislé na počítači, kde je zobrazení stránky a co požadavky jsou včetně.  
  
 Publish.htm; je název výchozí webové stránky můžete změnit název v **Návrháře projektu**. Další informace najdete v tématu [postupy: určení stránky publikování pro aplikaci ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).  
  
 Publish.htm – webová stránka je publikován pouze v případě, že byla zjištěna novější verze.  
  
> [!NOTE]
>  Změny provedené na vaše **publikovat** nastavení nebude mít vliv na stránce Publish.htm s jednou výjimkou: Pokud přidáte nebo odeberete požadavky po počátečním publikování, seznam požadovaných součástí nebudou přesné. Je potřeba upravit text pro požadovaný odkaz tak, aby odrážely změny.  
  
### <a name="to-customize-the-publish-web-page"></a>Chcete-li přizpůsobit publikované webové stránky  
  
1.  Publikování aplikace ClickOnce k umístění webu. Další informace najdete v tématu [postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
2.  Na webovém serveru otevřete soubor Publish.htm v Visual Web Designer nebo jiného editoru HTML.  
  
3.  Přizpůsobení stránky podle potřeby a uložte ho.  
  
4.  Volitelné. Chcete-li zabránit přepsání publikovat vlastní webovou stránku sady Visual Studio, zrušte zaškrtnutí políčka **automaticky generovat webovou stránku nasazení po každé publikovat** v dialogovém okně Možnosti publikování.  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)   
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Postupy: instalace předpokladů s aplikací ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Postupy: Určení stránky publikování pro aplikaci ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)



