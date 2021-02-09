---
title: Výběr strategie nasazení ClickOnce | Microsoft Docs
description: Přečtěte si o strategiích pro nasazení aplikace ClickOnce a o tom, jak zvolit strategii v závislosti na typu aplikace, kterou nasazujete.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, strategies
- deploying applications, ClickOnce
ms.assetid: 98bcab65-ab8b-4ed1-9adc-fdacf92b8106
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f4c20689c79529edf4a34edca857dedf1420b03f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895112"
---
# <a name="choose-a-clickonce-deployment-strategy"></a>Výběr strategie nasazení ClickOnce
Existují tři různé strategie pro nasazení aplikace. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] strategie, kterou zvolíte, závisí hlavně na typu aplikace, kterou nasazujete. Toto jsou zmíněné tři strategie nasazení:

- Instalace z webu nebo sdíleného síťového umístění

- Instalace z disku CD

- Spuštění aplikace z webu nebo sdíleného síťového umístění

    > [!NOTE]
    > Kromě výběru strategie nasazení budete chtít zvolit také strategii pro poskytování aktualizací aplikace. Další informace najdete v tématu [volba strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

## <a name="install-from-the-web-or-a-network-share"></a>Instalace z webu nebo sdílené síťové složky
 Použijete-li tuto strategii, vaše aplikace bude nasazena na webový server nebo do sdíleného síťového umístění. Chce-li koncový uživatel instalovat aplikaci, klikne na ikonu na webové stránce nebo dvakrát klikne na ikonu ve sdíleném umístění. Aplikace je poté stažena, nainstalována a spuštěna v počítači koncového uživatele. Položky jsou přidány do nabídky **Start** a **Přidat nebo odebrat programy** v **Ovládacích panelech**.

 Vzhledem k tomu, že tato strategie závisí na možnosti připojení k síti, je nejvhodnější pro aplikace, které budou nasazeny pro uživatele s přístupem k místní síti nebo s vysokorychlostním připojením k internetu.

 Pokud nasazujete aplikace z webu, můžete předat argumenty do aplikace při aktivaci pomocí adresy URL. Další informace naleznete v tématu [How to: načíst informace řetězce dotazu v online aplikaci ClickOnce](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md). Argumenty nelze předávat do aplikace, která se aktivuje pomocí jakýchkoli jiných metod popsaných v tomto dokumentu.

 Chcete-li povolit tuto strategii nasazení v nástroji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , klikněte na možnost **z webu** nebo **z cesty UNC nebo sdílené složky** na stránce **jak je nainstalován** Průvodce publikováním.

 Toto je výchozí strategie nasazení.

## <a name="start-the-application-from-the-web-or-a-network-share"></a>Spuštění aplikace z webu nebo sdílené síťové složky
 Tato strategie je stejná jako první zmíněná strategie, s výjimkou toho, že aplikace se chová jako webová aplikace. Pokud uživatel klikne na odkaz na webové stránce (nebo dvakrát klikne na ikonu ve sdíleném umístění), aplikace se spustí. Když uživatelé aplikaci zavřou, už nejsou k dispozici na svém místním počítači. do nabídky **Start** není nic přidáno ani **Přidat nebo odebrat programy** v **Ovládacích panelech**.

> [!NOTE]
> Z technického hlediska je aplikace stažena a nainstalována do mezipaměti aplikací na místním počítači stejně tak, jako je webová aplikace stažena do mezipaměti webu. Podobně jakou u mezipaměti webu jsou soubory nakonec z mezipaměti aplikací odstraněny. Uživatel však má dojem, že aplikace je spuštěna z webu nebo sdíleného umístění.

 Tato strategie je nejvhodnější pro aplikace, které se používají zřídka – příkladem je nástroj pro zaměstnanecké výhody, který se obvykle spouští pouze jednou ročně.

 Chcete-li povolit tuto strategii nasazení v nástroji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , klikněte na možnost **neinstalovat aplikaci** na stránce **instalovat nebo spustit z webové** stránky průvodce publikováním.

 Chcete-li tuto strategii nasazení povolit ručně, změňte značku **instalace** v manifestu nasazení. (Jeho hodnota může být **true** nebo **false**. V *Mage.exe* použijte možnost **pouze online** v seznamu **Typ aplikace** .)

## <a name="install-from-a-cd"></a>Instalace z disku CD
 Použijete-li tuto strategii, vaše aplikace bude nasazena na vyměnitelné médium, jako je například disk CD-ROM nebo DVD. Stejně jako u předchozí možnosti platí, že když uživatel zvolí instalaci aplikace, nainstaluje a spustí a položky se přidají do nabídky **Start** a **Přidat nebo odebrat programy** v **Ovládacích panelech**.

 Tato strategie je nejvhodnější pro aplikace, které budou nasazeny pro uživatele bez možnosti trvalého připojení k síti nebo s malou šířkou pásma připojení. Vzhledem k tomu, že aplikace se instaluje z vyměnitelných médií, není pro instalaci vyžadováno žádné síťové připojení. Možnost připojení k síti je však stále zapotřebí z důvodu aktualizací aplikace.

 Chcete-li povolit tuto strategii nasazení v nástroji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , klikněte na možnost **z disku CD-ROM nebo DVD-ROM** na stránce **jak je nainstalován** Průvodce publikováním.

 Chcete-li tuto strategii nasazení povolit ručně, změňte značku **deploymentProvider** v manifestu nasazení. (V aplikaci Visual Studio je tato vlastnost vystavena jako **Adresa URL instalace** na stránce **publikovat** v Návrháři projektu. V *Mage.exe* je **počáteční umístění**.)

## <a name="web-browser-support"></a>Podpora webového prohlížeče
 Aplikace určené pro platformu .NET Framework 3.5 mohou být nainstalovány pomocí libovolného prohlížeče.

 Aplikace určené pro rozhraní .NET Framework 2.0 vyžadují prohlížeč Internet Explorer.

## <a name="see-also"></a>Viz také
- [Zabezpečení a nasazení ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Výběr strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)