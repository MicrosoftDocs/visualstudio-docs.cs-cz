---
title: Stránka publikování, Návrhář projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.PropertyPage
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Project Designer, Publish page
- Publish page in Project Designer
ms.assetid: 153527c6-8b95-4003-8e8e-03a489d0a629
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 391e6c457dd09afa154c46cbc8644f028052cb32
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665709"
---
# <a name="publish-page-project-designer"></a>Publikovat stránku, návrhář projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Stránka **publikovat** v **Návrháři projektu** se používá ke konfiguraci vlastností pro nasazení ClickOnce.

 Pro přístup ke stránce **publikovat** vyberte uzel projektu v **Průzkumník řešení**a potom v nabídce **projekt** klikněte na **vlastnosti**. Když se zobrazí **Návrhář projektu** , klikněte na kartu **publikovat** .

> [!NOTE]
> Některé vlastnosti ClickOnce popsané tady lze také nastavit v **PublishWizard**, k dispozici v nabídce **sestavení** nebo kliknutím na tlačítko **PublishWizard** na této stránce.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní
 **Umístění složky pro publikování** Určuje umístění, kde je aplikace publikována. Může se jednat o cestu k jednotce ( `C:\deploy\myapplication` ), sdílenou složku (), `\\server\myapplication` Server FTP ( `ftp://ftp.microsoft.com/myapplication` ) nebo web ( `http://www.microsoft.com/myapplication` ). Všimněte si, že text musí být přítomen v poli **umístění pro publikování** , aby tlačítko Procházet (**...**) fungovalo.

 Ve výchozím nastavení je umístění publikování v `http://localhost/<projectname>/` případě, že máte nainstalovanou službu IIS, nebo `publish\` adresář, pokud nemáte NAINSTALOVANOU službu IIS. Pokud je v počítači spuštěný systém Windows Vista, výchozí hodnota je vždy `publish\` adresář bez ohledu na to, zda je nainstalována služba IIS.

 **Adresa URL instalační složky** Volitelné. Určuje web, na který uživatelé přejdou instalovat aplikaci. To je nezbytné jenom v případě, že se liší od **umístění pro publikování**, například při publikování aplikace na přípravném serveru.

 **Režim instalace a nastavení** Určuje, zda je aplikace spuštěna přímo z **umístění pro publikování** (Pokud je **aplikace dostupná pouze online** ), nebo je nainstalována a přidána do nabídky **Start** a položky **Přidat nebo odebrat programy** v **Ovládacích panelech** (Pokud **je aplikace dostupná také v režimu offline** ).

 Pro aplikace webového prohlížeče WPF **je aplikace k dispozici offline** a možnost je zakázána, protože tyto aplikace jsou k dispozici pouze online.

 **Soubory aplikace** Otevře [dialogové okno soubory aplikace](https://msdn.microsoft.com/b06dff3a-b87a-4caf-996b-7a4acf8137a8), které slouží k určení toho, jak a kde jsou jednotlivé soubory nainstalovány.

 **Požadavky** Otevře [dialogové okno požadavky](../../ide/reference/prerequisites-dialog-box.md), které se používá k určení požadovaných součástí, jako je například .NET Framework, aby se nainstalovaly společně s aplikací.

 **Aktualizace** Otevře [dialogové okno aktualizace aplikace](https://msdn.microsoft.com/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f), které slouží k určení chování aktualizace pro aplikaci. Tato možnost není dostupná, pokud **je aplikace dostupná jenom online** .

 **Možnosti** Otevře [dialogové okno Možnosti publikování](https://msdn.microsoft.com/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), které slouží k určení dalších pokročilých možností publikování.

 **Verze publikování** Nastaví číslo verze publikování pro aplikaci. Když se změní číslo verze, aplikace se publikuje jako aktualizace. Každá část verze publikování (**Hlavní**, **podverze**, **sestavení**, **Revize**) může mít maximální hodnotu 65355 ( <xref:System.UInt16.MaxValue> ), což je maximální povolený <xref:System.Version> .

 Při instalaci více než jedné verze aplikace pomocí technologie ClickOnce instalační program přesune předchozí verze aplikace do složky s názvem Archive v umístění pro publikování, které zadáte. Archivace předchozích verzí tímto způsobem udržuje instalační adresář v nejasnosti od předchozí verze.

 **Automaticky zvyšovat revize při každém publikování** Volitelné. Pokud je vybrána tato možnost (výchozí nastavení), část **Revize** čísla verze publikování se zvýší o jednu pokaždé, když je aplikace publikována. To způsobí, že se aplikace publikuje jako aktualizace.

 **Průvodce publikováním** Otevře [Průvodce publikováním](https://msdn.microsoft.com/fc6abebd-13d6-48e4-a567-fbc52dad0872). Dokončení Průvodce publikováním má stejný účinek jako spuštění příkazu **publikovat** v nabídce **sestavení** .

 **Publikovat hned** Publikuje aplikaci pomocí aktuálního nastavení. Odpovídá tlačítku **Dokončit** v **PublishWizard**.

## <a name="see-also"></a>Viz také
 [Publikování aplikací ClickOnce](../../deployment/publishing-clickonce-applications.md) [Postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) [Postupy: určení místa, kde aplikace Visual Studio kopíruje soubory](../../deployment/how-to-specify-where-visual-studio-copies-the-files.md) [Postupy: určení umístění, do kterého budou koncoví uživatelé instalovat z](../../deployment/how-to-specify-the-location-where-end-users-will-install-from.md) tématu [Postupy: určení odkazu pro technickou podporu](../../deployment/how-to-specify-a-link-for-technical-support.md) [Postupy: určení odkazu na režim offline nebo online instalace](../../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md) [Postupy: povolení automatického spuštění pro instalaci CD](../../deployment/how-to-enable-autostart-for-cd-installations.md) [Postupy: nastavení publikační verze ClickOnce](../../deployment/how-to-set-the-clickonce-publish-version.md) [Postupy: automatické zvýšení verze publikování ClickOnce](../../deployment/how-to-automatically-increment-the-clickonce-publish-version.md) postupy: [Určení souborů, které jsou publikovány pomocí technologie ClickOnce](../../deployment/how-to-specify-which-files-are-published-by-clickonce.md) [Postupy: instalace požadavků s aplikací ClickOnce](../../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) [Postupy: Správa aktualizací pro aplikaci ClickOnce](../../deployment/how-to-manage-updates-for-a-clickonce-application.md) [Postupy: Změna jazyka publikování pro](../../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md) aplikaci ClickOnce postupy: [určení názvu nabídky Start pro aplikaci](../../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md) [ClickOnce postupy : Určení stránky publikování pro](../../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md) [zabezpečení a nasazení](../../deployment/clickonce-security-and-deployment.md) ClickOnce aplikace ClickOnce
