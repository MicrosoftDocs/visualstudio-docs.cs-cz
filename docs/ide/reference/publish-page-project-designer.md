---
title: Publikovat stránku, návrhář projektu
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.PropertyPage
helpviewer_keywords:
- Project Designer, Publish page
- Publish page in Project Designer
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bbb43408dc12c55b72eb0ca0909d8b261198a5b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "68926174"
---
# <a name="publish-page-project-designer"></a>Publikovat stránku, návrhář projektu

Stránka **Publikovat** **Návrháře projektu** slouží ke konfiguraci vlastností pro nasazení ClickOnce.

Chcete-li získat přístup ke stránce **Publikovat,** vyberte uzel projektu v **Průzkumníku řešení**a v nabídce **Project** klepněte na příkaz **Vlastnosti**. Po zobrazení **Návrháře projektů** klikněte na kartu **Publikovat.**

> [!NOTE]
> Některé zde popsané vlastnosti ClickOnce lze také nastavit v **Průvodci publikováním**, který je k dispozici v nabídce **Sestavení** nebo klepnutím na tlačítko **PublishWizard** na této stránce.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

 **Umístění složky publikování**

Určuje umístění, kde je aplikace publikována. Může se pokládat`C:\deploy\myapplication`cesta jednotky`\\server\myapplication`( ), sdílená`ftp://ftp.microsoft.com/myapplication`složka souboru ( ) nebo server FTP ( ). Všimněte si, že text musí být přítomen v poli **Umístění publikování,** aby tlačítko procházení (**...**) fungovalo.

 **Adresa URL instalační složky**

Nepovinný parametr. Určuje web, na který uživatelé přejít k instalaci aplikace. To je nezbytné pouze v případě, že se liší od **umístění publikování**, například při publikování aplikace na pracovní server.

 **Režim instalace a nastavení**

Určuje, zda je aplikace spuštěna přímo z **umístění publikování** (pokud **je vybrána aplikace dostupná pouze online)** nebo zda je nainstalována a přidána do nabídky **Start** a **v Ovládacích panelech** **Přidat nebo odebrat programy** (pokud je aplikace k dispozici také **offline).**

Pro wpf webového prohlížeče aplikace **aplikace je k dispozici offline, stejně** jako možnost je zakázána, protože tyto aplikace jsou k dispozici pouze online.

 **Soubory aplikací**

Otevře dialogové okno Soubory aplikace, které slouží k určení způsobu a umístění jednotlivých souborů.

 **Požadavky**

Otevře dialogové okno Požadavky, které slouží k určení nezbytných součástí, jako je například rozhraní .NET Framework, které mají být nainstalovány společně s aplikací.

 **Aktualizace**

Otevře dialogové okno Aktualizace aplikace, které slouží k určení chování aktualizace aplikace. Není k dispozici, pokud **je aplikace k dispozici pouze online.**

 **Možnosti**

Otevře dialogové okno Možnosti publikování, které slouží k určení dalších upřesňujících možností publikování.

 **Publikovat verzi**

Nastaví číslo verze publikování pro aplikaci. při změně čísla verze je aplikace publikována jako aktualizace. Každá část verze publikování (**Hlavní**, **Vedlejší**, **Build**, **Revize**) může<xref:System.UInt16.MaxValue>mít maximální <xref:System.Version>hodnotu 65355 ( ), maximální povoleno .

Při instalaci více než jednu verzi aplikace pomocí ClickOnce, instalace přesune starší verze aplikace do složky s názvem Archiv, v umístění publikování, které zadáte. Archivace starších verzí tímto způsobem udržuje instalační adresář bez složek z předchozí verze.

 **Automatická revize přírůstku s každým publikováním**

Nepovinný parametr. Je-li vybrána tato možnost (výchozí), část **Revize** čísla verze publikování se při každém publikování aplikace zvětší o jednu. To způsobí, že aplikace bude publikována jako aktualizace.

 **Průvodce publikováním**

Otevře Průvodce publikováním. Dokončení Průvodce publikováním má stejný účinek jako spuštění příkazu **Publikovat** v nabídce **Sestavení.**

 **Publikovat nyní**

Publikuje aplikaci pomocí aktuálního nastavení. Ekvivalentní tlačítko **Dokončit** v **Průvodci publikováním**.

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
- [ClickOnce Zabezpečení a nasazení](../../deployment/clickonce-security-and-deployment.md)
