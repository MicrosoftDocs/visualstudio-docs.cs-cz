---
title: Publikovat stránku, návrhář projektu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.PropertyPage
helpviewer_keywords:
- Project Designer, Publish page
- Publish page in Project Designer
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 894328fed089ea631af41f7aa7ef1f08d6dc4d8f
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2018
ms.locfileid: "39179499"
---
# <a name="publish-page-project-designer"></a>Publikovat stránku, návrhář projektu
**Publikovat** stránku **Návrháře projektu** slouží ke konfiguraci vlastností pro nasazení ClickOnce.

 Pro přístup **publikovat** stránky, vyberte uzel projektu v **Průzkumníku řešení**a pak klikněte na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. Když **Návrháře projektu** se zobrazí, klikněte na tlačítko **publikovat** kartu.

> [!NOTE]
> Některé vlastnosti ClickOnce je zde popsáno, můžete také nastavit v **PublishWizard**, která je dostupná z **sestavení** nabídek nebo kliknutím **PublishWizard** na toto tlačítko stránka.


## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní
 **Umístění složky pro publikování**

 Určuje umístění, kde je aplikace publikována. Může být cesta jednotky (`C:\deploy\myapplication`), sdílené složky (`\\server\myapplication`), nebo FTP server (`ftp://ftp.microsoft.com/myapplication`). Všimněte si, že text musí být součástí **umístění pro publikování** pole mohl procházet (**...** ) tlačítko pro práci.

 **Adresa URL složky instalace**

 Volitelné. Určuje web, ke kterému uživatelé přejít k instalaci aplikace. To je nezbytné, jenom když se liší od **umístění pro publikování**, například při publikování aplikace na testovacím serveru.

 **Režim instalace a nastavení**

 Určuje, zda je aplikace spuštěna přímo z **umístění pro publikování** (když **aplikace je dostupná pouze online** je vybraná) nebo je nainstalován a přidán do **Start**  nabídky a **přidat nebo odebrat programy** položky v **ovládací panely** (když **aplikace je k dispozici také v režimu offline** je vybrána).

 Pro aplikace pro WPF webového prohlížeče **aplikace je k dispozici také v režimu offline** možnost je zakázána, protože tyto aplikace jsou k dispozici pouze online.

 **Soubory aplikace**

 Otevře dialogové okno souborů aplikace, které slouží k určení, jak a kde jsou nainstalovány jednotlivé soubory.

 **Požadované součásti**

 Otevře se dialogové okno požadavky, které slouží k určení požadovaných součástí, jako je například rozhraní .NET Framework nainstalovat spolu s aplikací.

 **Aktualizace**

 Otevře dialogové okno aktualizace aplikace, které slouží k určení chování aktualizací pro aplikaci. Nejsou k dispozici při **aplikace je dostupná pouze online** zaškrtnuto.

 **Možnosti**

 Otevře dialogové okno Možnosti publikování, který se používá k určení dalších rozšířené možnosti publikování.

 **Verze publikování**

 Nastaví číslo verze publikování pro aplikaci. Při změně číslo verze aplikace publikována jako aktualizace. Každá část verzi publikování (**hlavní**, **menší**, **sestavení**, **revize**) může mít maximální hodnotu 65355 (<xref:System.UInt16.MaxValue>), maximální povolenou <xref:System.Version>.

 Při instalaci více než jednu verzi aplikace s použitím technologie ClickOnce, instalace přesune starší verze této aplikace do složky s názvem Archiv v umístění pro publikování, který zadáte. Archivace dřívějších verzí tímto způsobem udržuje instalační adresář čistý od složek starší verze.

 **Automaticky zvyšovat číslo při každém publikování**

 Volitelné. Když je vybraná tato možnost (výchozí), **revize** část čísla verze publikování se zvýší o jedna pokaždé, když je aplikace publikována. To způsobí, že aplikace má být publikován jako aktualizace.

 **Průvodce publikováním**

 Otevře Průvodce publikováním. Dokončuje se Průvodce publikováním má stejný účinek jako spuštění **publikovat** příkaz **sestavení** nabídky.

 **Publikovat**

 Publikuje aplikace s použitím aktuální nastavení. Ekvivalentní **Dokončit** tlačítko **PublishWizard**.

## <a name="see-also"></a>Viz také

- [Publikování aplikací ClickOnce](../../deployment/publishing-clickonce-applications.md)
- [Postupy: Publikování aplikace ClickOnce pomocí průvodce publikováním](../../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Postupy: Určení cíle kopírování souborů sadou Visual Studio](../../deployment/how-to-specify-where-visual-studio-copies-the-files.md)
- [Postupy: Určení umístění, z něhož mohou instalovat koncoví uživatelé](../../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)
- [Postupy: Určení obsahu pro technickou podporu](../../deployment/how-to-specify-a-link-for-technical-support.md)
- [Postupy: Určení offline nebo online režimu instalace ClickOnce](../../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)
- [Postupy: Povolení funkce AutoStart pro instalace z média CD](../../deployment/how-to-enable-autostart-for-cd-installations.md)
- [Postupy: Nastavení verze publikování ClickOnce](../../deployment/how-to-set-the-clickonce-publish-version.md)
- [Postupy: Automatická inkrementace verze publikování ClickOnce](../../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [Postupy: Určení souborů k publikování aplikací ClickOnce](../../deployment/how-to-specify-which-files-are-published-by-clickonce.md)
- [Postupy: Instalace předpokladů s aplikací ClickOnce](../../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Postupy: Správa aktualizací pro aplikaci ClickOnce](../../deployment/how-to-manage-updates-for-a-clickonce-application.md)
- [Postupy: Změna jazyka publikování pro aplikaci ClickOnce](../../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)
- [Postupy: Určení názvu úvodní nabídky pro aplikaci ClickOnce](../../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)
- [Postupy: Určení stránky publikování pro aplikaci ClickOnce](../../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)
- [ClickOnce – zabezpečení a nasazení](../../deployment/clickonce-security-and-deployment.md)
