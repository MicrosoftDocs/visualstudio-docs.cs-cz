---
title: Publikování aplikací ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Options
- Microsoft.VisualStudio.Publish.ClickOnceProvider.PublishWizard.Help
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- ClickOnce applications, publishing
- applications [Visual Studio], ClickOnce deployment
- deploying applications [ClickOnce], publishing ClickOnce applications
ms.assetid: eb6dfe79-f54c-4331-8e36-073688e70973
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41cd62e8831ac4edd5b37337c1e72dd0b2e662e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85536289"
---
# <a name="publish-clickonce-applications"></a>Publikování aplikací ClickOnce
Při prvním publikování [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace lze vlastnosti publikování nastavit pomocí Průvodce publikováním. V průvodci jsou k dispozici pouze některé vlastnosti. všechny ostatní vlastnosti jsou nastaveny na výchozí hodnoty.

 Následné změny vlastností publikování jsou provedeny na stránce **publikovat** v **Návrháři projektu**.

## <a name="publish-wizard"></a>Průvodce publikováním
 K nastavení základního nastavení pro publikování aplikace můžete použít Průvodce publikováním. To zahrnuje následující vlastnosti publikování:

- Umístění složky pro publikování – kde aplikace Visual Studio bude kopírovat soubory (místní počítač, síťová sdílená složka, server FTP nebo Web)

- Umístění instalační složky – kam se budou koncoví uživatelé instalovat (síťová sdílená složka, server FTP, web, CD/DVD)

- Online nebo offline dostupnost – Pokud koncoví uživatelé mají přístup k aplikaci s nebo bez připojení k síti

- Frekvence aktualizace – jak často aplikace kontroluje nové aktualizace.

  Další informace naleznete v tématu [How to: Publish a aplikace ClickOnce using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

## <a name="publish-page"></a>Stránka Publikovat
 Stránka **publikovat** v **Návrháři projektu** se používá ke konfiguraci vlastností pro nasazení ClickOnce. V následující tabulce jsou uvedena témata.

|Nadpis|Popis|
|-----------|-----------------|
|[Postupy: určení umístění, kam aplikace Visual Studio kopíruje soubory](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)|Popisuje, jak nastavit, kde aplikace Visual Studio vloží soubory aplikace a manifesty.|
|[Postupy: určení umístění, z něhož budou koncoví uživatelé instalovat](../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)|Popisuje, jak nastavit umístění, kam uživatelé přejdou stáhnout a nainstalovat aplikaci.|
|[Postupy: určení offline nebo online režimu instalace ClickOnce](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)|Popisuje, jak nastavit, zda bude aplikace k dispozici offline nebo online.|
|[Postupy: nastavení verze publikování ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)|Popisuje, jak nastavit vlastnost **verze publikování** ClickOnce, která určuje, zda bude aplikace, kterou publikujete, považována za aktualizaci.|
|[Postupy: automatické zvýšení verze publikování ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)|Popisuje, jak automaticky zvyšovat číslo revize **PublishVersion** pokaždé, když publikujete aplikaci.|

 Další informace naleznete v tématu [publikování stránky, Návrhář projektu](../ide/reference/publish-page-project-designer.md)

### <a name="application-files-dialog-box"></a>Dialogové okno soubory aplikace
 Toto dialogové okno umožňuje určit, jak jsou soubory v projektu zařazeny do kategorií pro publikování, dynamické stahování a aktualizace. Obsahuje mřížku, která obsahuje seznam souborů projektu, které nejsou ve výchozím nastavení vyloučené nebo které mají skupinu pro stažení.

 Chcete-li vyloučit soubory, označit soubory jako datové soubory nebo předpoklady a vytvořit skupiny souborů pro podmíněnou instalaci v uživatelském rozhraní sady Visual Studio, přečtěte si téma [How to: Určete, které soubory jsou publikovány pomocí technologie ClickOnce](../deployment/how-to-specify-which-files-are-published-by-clickonce.md). Datové soubory můžete také označit pomocí Mage.exe. Další informace naleznete v tématu [How to: include a data File in a ClickOnce Application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).

### <a name="prerequisites-dialog-box"></a>dialogové okno Požadavky
 Toto dialogové okno určuje, které požadované součásti jsou nainstalovány, a také způsob jejich instalace. Další informace naleznete v tématu [How to: Install – požadavky v](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) [dialogovém okně](../ide/reference/prerequisites-dialog-box.md)aplikace ClickOnce a požadavky.

### <a name="application-updates-dialog-box"></a>Dialogové okno aktualizace aplikace
 Toto dialogové okno určuje, jak má instalace aplikace vyhledat aktualizace. Další informace naleznete v tématu [How to: Manage Updates for a ClickOnce Application](../deployment/how-to-manage-updates-for-a-clickonce-application.md).

### <a name="publish-options-dialog-box"></a>Dialogové okno Možnosti publikování
 Dialogové okno Možnosti publikování Určuje možnosti nasazení aplikace.

|Nadpis|Popis|
|-|-|
|[Postupy: Změna jazyka publikování pro aplikaci ClickOnce](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)|Popisuje, jak zadat jazyk a jazykovou verzi odpovídající lokalizované verzi.|
|[Postupy: určení názvu nabídky Start pro aplikaci ClickOnce](../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)|Popisuje, jak změnit zobrazovaný název aplikace ClickOnce.|
|[Postupy: určení odkazu na technickou podporu](../deployment/how-to-specify-a-link-for-technical-support.md)|Popisuje, jak nastavit vlastnost **adresy URL podpory** , která identifikuje webovou stránku nebo sdílenou složku, kde mohou uživatelé přejít k získání informací o aplikaci.|
|[Postupy: určení adresy URL pro podporu pro jednotlivé předpoklady v nasazení ClickOnce](../deployment/how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment.md)|Ukázala, jak ručně změnit manifest aplikace tak, aby zahrnovaly adresy URL jednotlivých žádostí o podporu pro jednotlivé požadavky.|
|[Postupy: určení stránky publikování pro aplikaci ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)|Popisuje, jak vygenerovat a publikovat výchozí webovou stránku (publish.htm) společně s aplikací.|
|[Postupy: přizpůsobení výchozí webové stránky ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)|Popisuje, jak přizpůsobit webovou stránku, která je automaticky generovaná a publikovaná spolu s aplikací.|
|[Postupy: povolení funkce Autostart pro instalace z disku CD](../deployment/how-to-enable-autostart-for-cd-installations.md)|Popisuje, jak povolit autostart, aby se aplikace ClickOnce automaticky spustila při vložení média.|

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Postupy: vytváření přidružení souborů pro aplikaci ClickOnce](../deployment/how-to-create-file-associations-for-a-clickonce-application.md)|Popisuje, jak přidat podporu přípon názvů souborů do aplikace ClickOnce.|
|[Postupy: načtení informací řetězce dotazu v online aplikaci ClickOnce](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)|Ukazuje, jak načíst parametry předané v adrese URL použité ke spuštění aplikace ClickOnce.|
|[Postupy: zákaz aktivace adresy URL aplikací ClickOnce pomocí návrháře](../deployment/how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer.md)|Popisuje, jak vynutit, aby uživatelé spustili aplikaci z nabídky **Start** pomocí návrháře.|
|[Postupy: zákaz aktivace adresy URL aplikací ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)|Popisuje, jak vynutit, aby uživatelé spustili aplikaci z nabídky **Start** .|
|[Návod: stahování sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce pomocí návrháře](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)|Vysvětluje, jak stáhnout sestavení aplikace pouze v případě, že je aplikace nejprve používána pomocí návrháře.|
|[Návod: stažení sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Vysvětluje, jak stáhnout sestavení aplikace pouze při jejich prvním použití aplikací.|
|[Návod: Stahování satelitních sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Popisuje, jak označit vaše satelitní sestavení jako volitelné a stáhnout pouze sestavení, které klientský počítač potřebuje pro aktuální nastavení jazykové verze.|
|[Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)|Vysvětluje, jak použít nástroje .NET Framework k nasazení aplikace ClickOnce.|
|[Návod: Ruční nasazení aplikace ClickOnce, která nevyžaduje Opětovné podepsání a které zachovává informace o značkách](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)|Vysvětluje, jak použít nástroje .NET Framework k nasazení aplikace ClickOnce bez opětovného podepsání manifestů.|
|[Postupy: konfigurace projektů pro cílové platformy](../ide/how-to-configure-projects-to-target-platforms.md)|Vysvětluje, jak publikovat pro 64 procesor změnou **cílové vlastnosti procesoru** nebo **cílové platformy** ve vašem projektu.|
|[Návod: povolení spuštění aplikace ClickOnce na více verzích .NET Framework](https://msdn.microsoft.com/library/7f4383af-ed87-4853-b4d4-02a3967a5fd9)|Vysvětluje, jak povolit aplikaci ClickOnce k instalaci a spuštění na více verzích rozhraní .NET Framework.|
|[Návod: Vytvoření vlastního instalačního programu pro aplikaci ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)|Vysvětluje, jak vytvořit vlastní instalační program pro instalaci aplikace ClickOnce.|
|[Postupy: publikování aplikace WPF s povolenými vizuálními styly](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)|Obsahuje podrobné pokyny pro řešení chyby, jež se zobrazí při pokusu o publikování aplikace WPF, která má povoleny vizuální styly.|

## <a name="see-also"></a>Viz také
- [Zabezpečení a nasazení ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Odkaz na ClickOnce](../deployment/clickonce-reference.md)
