---
title: Publikovat stránku, návrhář projektu
description: Stránka publikovat v Návrháři projektu se používá ke konfiguraci vlastností pro nasazení ClickOnce.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 13edc1b2e2e235eaf5a475764a98067aa4b0150d
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350280"
---
# <a name="publish-page-project-designer"></a>Publikovat stránku, návrhář projektu

Stránka **publikovat** v **Návrháři projektu** se používá ke konfiguraci vlastností pro nasazení ClickOnce.

Pro přístup ke stránce **publikovat** vyberte uzel projektu v **Průzkumník řešení** a potom v nabídce **projekt** klikněte na **vlastnosti**. Když se zobrazí **Návrhář projektu** , klikněte na kartu **publikovat** .

> [!NOTE]
> Některé vlastnosti ClickOnce popsané tady lze také nastavit v **PublishWizard** , k dispozici v nabídce **sestavení** nebo kliknutím na tlačítko **PublishWizard** na této stránce.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

 **Umístění složky pro publikování**

Určuje umístění, kde je aplikace publikována. Může se jednat o cestu k jednotce ( `C:\deploy\myapplication` ), sdílenou složku ( `\\server\myapplication` ) nebo server FTP ( `ftp://ftp.microsoft.com/myapplication` ). Všimněte si, že text musí být přítomen v poli **umístění pro publikování** , aby tlačítko Procházet ( **...** ) fungovalo.

 **Adresa URL instalační složky**

Nepovinný parametr. Určuje web, na který uživatelé přejdou instalovat aplikaci. To je nezbytné jenom v případě, že se liší od **umístění pro publikování** , například při publikování aplikace na přípravném serveru.

 **Režim instalace a nastavení**

Určuje, zda je aplikace spuštěna přímo z **umístění pro publikování** (Pokud je **aplikace dostupná pouze online** ), nebo je nainstalována a přidána do nabídky **Start** a položky **Přidat nebo odebrat programy** v **Ovládacích panelech** (Pokud **je aplikace dostupná také v režimu offline** ).

Pro aplikace webového prohlížeče WPF **je aplikace k dispozici offline** a možnost je zakázána, protože tyto aplikace jsou k dispozici pouze online.

 **Soubory aplikace**

Otevře dialogové okno soubory aplikace, které slouží k určení toho, jak a kde jsou jednotlivé soubory nainstalovány.

 **Požadavky**

Otevře dialogové okno požadavky, které se používá k určení požadovaných součástí, jako je například .NET Framework, aby se nainstalovaly společně s aplikací.

 **Aktualizace**

Otevře dialogové okno aktualizace aplikace, které slouží k určení chování aktualizace pro aplikaci. Tato možnost není dostupná, pokud **je aplikace dostupná jenom online** .

 **Možnosti**

Otevře dialogové okno Možnosti publikování, které slouží k určení dalších pokročilých možností publikování.

 **Verze publikování**

Nastaví číslo verze publikování pro aplikaci. Když se změní číslo verze, aplikace se publikuje jako aktualizace. Každá část verze publikování ( **Hlavní** , **podverze** , **sestavení** , **Revize** ) může mít maximální hodnotu 65355 ( <xref:System.UInt16.MaxValue> ), což je maximální povolený <xref:System.Version> .

Při instalaci více než jedné verze aplikace pomocí technologie ClickOnce instalační program přesune předchozí verze aplikace do složky s názvem Archive v umístění pro publikování, které zadáte. Archivace předchozích verzí tímto způsobem udržuje instalační adresář v nejasnosti od předchozí verze.

 **Automaticky zvyšovat revize při každém publikování**

Nepovinný parametr. Pokud je vybrána tato možnost (výchozí nastavení), část **Revize** čísla verze publikování se zvýší o jednu pokaždé, když je aplikace publikována. To způsobí, že se aplikace publikuje jako aktualizace.

 **Průvodce publikováním**

Otevře Průvodce publikováním. Dokončení Průvodce publikováním má stejný účinek jako spuštění příkazu **publikovat** v nabídce **sestavení** .

 **Publikovat hned**

Publikuje aplikaci pomocí aktuálního nastavení. Odpovídá tlačítku **Dokončit** v **PublishWizard**.

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
