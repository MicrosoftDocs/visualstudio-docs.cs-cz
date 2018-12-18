---
title: Výběr strategie nasazení ClickOnce | Dokumentace Microsoftu
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
- ClickOnce deployment, strategies
- deploying applications, ClickOnce
ms.assetid: 98bcab65-ab8b-4ed1-9adc-fdacf92b8106
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 54bf4f58a4cfe8622e12b3808ea9f36c8cf1ee49
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175627"
---
# <a name="choosing-a-clickonce-deployment-strategy"></a>Výběr strategie nasazení ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Existují tři různé strategie pro nasazení [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace; strategie, kterou zvolíte, závisí především na typu aplikace, kterou nasazujete. Toto jsou zmíněné tři strategie nasazení:  
  
-   Instalace z webu nebo sdíleného síťového umístění  
  
-   Instalace z disku CD  
  
-   Spuštění aplikace z webu nebo sdíleného síťového umístění  
  
    > [!NOTE]
    >  Kromě výběru strategie nasazení budete chtít zvolit také strategii pro poskytování aktualizací aplikace. Další informace najdete v tématu [Výběr strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="install-from-the-web-or-a-network-share"></a>Instalace z webu nebo sdíleného síťového umístění  
 Použijete-li tuto strategii, vaše aplikace bude nasazena na webový server nebo do sdíleného síťového umístění. Chce-li koncový uživatel instalovat aplikaci, klikne na ikonu na webové stránce nebo dvakrát klikne na ikonu ve sdíleném umístění. Aplikace je poté stažena, nainstalována a spuštěna v počítači koncového uživatele. Položky jsou přidány do **Start** nabídky a **přidat nebo odebrat programy** v **ovládací panely**.  
  
 Vzhledem k tomu, že tato strategie závisí na možnosti připojení k síti, je nejvhodnější pro aplikace, které budou nasazeny pro uživatele s přístupem k místní síti nebo s vysokorychlostním připojením k internetu.  
  
 Pokud nasazujete aplikace z webu, můžete předat argumenty do aplikace při aktivaci pomocí adresy URL. Další informace najdete v tématu [postupy: načtení informací řetězce dotazu do Online aplikace ClickOnce](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md). Argumenty nelze předávat do aplikace, která se aktivuje pomocí jakýchkoli jiných metod popsaných v tomto dokumentu.  
  
 Chcete-li povolit tuto strategii nasazení v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], klikněte na tlačítko **z webu** nebo **ze sdílené složky UNC cestu nebo sdílená složka** na **způsob instalace** stránky v Průvodci publikováním.  
  
 Toto je výchozí strategie nasazení.  
  
## <a name="install-from-a-cd"></a>Instalace z disku CD  
 Použijete-li tuto strategii, vaše aplikace bude nasazena na vyměnitelné médium, jako je například disk CD-ROM nebo DVD. Stejně jako u předchozí možnosti platí, pokud uživatel zvolí možnost nainstalovat aplikaci, je nainstalovaný a spuštěný, a položky budou přidány do **Start** nabídky a **přidat nebo odebrat programy** v **ovládacího prvku Panel**.  
  
 Tato strategie je nejvhodnější pro aplikace, které budou nasazeny pro uživatele bez možnosti trvalého připojení k síti nebo s malou šířkou pásma připojení. Vzhledem k tomu, že aplikace se instaluje z vyměnitelných médií, není pro instalaci vyžadováno žádné síťové připojení. Možnost připojení k síti je však stále zapotřebí z důvodu aktualizací aplikace.  
  
 Chcete-li povolit tuto strategii nasazení v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], klikněte na tlačítko **z disku CD-ROM nebo DVD-ROM** na **způsob instalace** stránky v Průvodci publikováním.  
  
 Chcete-li tuto strategii nasazení povolit ručně, změňte **deploymentProvider** značky v manifestu nasazení. (V sadě Visual Studio, je tato vlastnost vystavena jako **adresa URL instalace** na **publikovat** stránky Návrháře projektu. V Mage.exe je **počáteční umístění**.)  
  
## <a name="start-the-application-from-the-web-or-a-network-share"></a>Spuštění aplikace z webu nebo sdíleného síťového umístění  
 Tato strategie je stejná jako první zmíněná strategie, s výjimkou toho, že aplikace se chová jako webová aplikace. Pokud uživatel klikne na odkaz na webové stránce (nebo dvakrát klikne na ikonu ve sdíleném umístění), aplikace se spustí. Když uživatelé aplikaci ukončí, již není k dispozici na místním počítači; nic není přidáno do **Start** nabídky nebo **přidat nebo odebrat programy** v **ovládací panely**.  
  
> [!NOTE]
>  Z technického hlediska je aplikace stažena a nainstalována do mezipaměti aplikací na místním počítači stejně tak, jako je webová aplikace stažena do mezipaměti webu. Podobně jakou u mezipaměti webu jsou soubory nakonec z mezipaměti aplikací odstraněny. Uživatel však má dojem, že aplikace je spuštěna z webu nebo sdíleného umístění.  
  
 Tato strategie je nejvhodnější pro aplikace, které se používají zřídka – příkladem je nástroj pro zaměstnanecké výhody, který se obvykle spouští pouze jednou ročně.  
  
 Chcete-li povolit tuto strategii nasazení v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], klikněte na tlačítko **neinstalujte aplikace** na **instalovat nebo spustit z webu** stránky v Průvodci publikováním.  
  
 Chcete-li tuto strategii nasazení povolit ručně, změňte **nainstalovat** značky v manifestu nasazení. (Jeho hodnota může být **true** nebo **false**. V Mage.exe, použijte **pouze Online** možnost **typ aplikace** seznamu.)  
  
## <a name="web-browser-support"></a>Podpora webového prohlížeče  
 Aplikace určené pro platformu .NET Framework 3.5 mohou být nainstalovány pomocí libovolného prohlížeče.  
  
 Aplikace určené pro rozhraní .NET Framework 2.0 vyžadují prohlížeč Internet Explorer.  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)   
 [Výběr strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Zabezpečování aplikací ClickOnce](../deployment/securing-clickonce-applications.md)



