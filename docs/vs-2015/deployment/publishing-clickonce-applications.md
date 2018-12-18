---
title: Publikování aplikací ClickOnce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 4282ce38671e2270c1e91d70df8968d790c54a22
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891762"
---
# <a name="publishing-clickonce-applications"></a>Publikování aplikací ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při publikování [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] vlastnosti publikování aplikace poprvé, můžete nastavit pomocí Průvodce publikováním. Pouze některé vlastnosti jsou k dispozici v Průvodci; všechny ostatní vlastnosti jsou nastavené na výchozí hodnoty.  
  
 Vlastnosti publikování následné změny probíhají v **publikovat** stránku **Návrháře projektu**.  
  
## <a name="publish-wizard"></a>Průvodce publikováním  
 Základní nastavení pro publikování aplikace, můžete použít Průvodce publikováním. To zahrnuje následující vlastnosti publikování:  
  
- Umístění složky pro publikování – kde aplikace Visual Studio zkopíruje soubory (místní počítač, sdíleného síťového umístění, FTP server nebo webové stránky)  
  
- Umístění složky instalace – koncoví uživatelé z něhož mohou instalovat (sdíleného síťového umístění, FTP server, webové stránky, disk CD/DVD)  
  
- Online nebo Offline dostupnost – Pokud se koncoví uživatelé můžou získat přístup k aplikaci s nebo bez připojení k síti  
  
- Aktualizace frekvence – jak často bude aplikace ověřovat nové aktualizace.  
  
  Další informace najdete v tématu [postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
## <a name="publish-page"></a>Stránka publikovat  
 **Publikovat** stránku **Návrháře projektu** slouží ke konfiguraci vlastností pro nasazení ClickOnce. V následující tabulce jsou uvedeny témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Určení cíle kopírování souborů sadou Visual Studio](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)|Popisuje, jak nastavit, kdy sady Visual Studio vloží soubory aplikace a manifesty.|  
|[Postupy: Určení umístění, z něhož mohou instalovat koncoví uživatelé](../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)|Popisuje, jak nastavit umístění, kde uživatelé ke stažení a instalaci aplikace.|  
|[Postupy: Určení offline nebo online režimu instalace ClickOnce](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)|Popisuje, jak nastavit, zda aplikace bude k dispozici online nebo offline.|  
|[Postupy: Nastavení verze publikování ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)|Popisuje, jak nastavit ClickOnce **publikovat verzi** vlastnost, která určuje, zda aplikace, které publikujete bude považována za aktualizace.|  
|[Postupy: Automatická inkrementace verze publikování ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)|Popisuje, jak automaticky zvýší číslo revize **PublishVersion** pokaždé, když publikujete aplikaci.|  
  
 Další informace najdete v tématu [publikovat stránku, Návrhář projektu](../ide/reference/publish-page-project-designer.md)  
  
### <a name="application-files-dialog-box"></a>Dialogové okno soubory aplikace  
 Toto dialogové okno umožňuje určit, jak jsou soubory ve vašem projektu zařazené do kategorií pro publikování, dynamické stažení a aktualizace. Obsahuje tabulku, ve které jsou uvedeny soubory projektu, které nejsou vyloučeny ve výchozím nastavení, nebo mají skupina pro stažení.  
  
 Vyloučit soubory, soubory označit jako datové soubory nebo požadavky a vytvářet skupiny podmíněné instalačním souborům v Uživatelském rozhraní aplikace Visual Studio, naleznete v tématu [postupy: určení který souborů k publikování aplikací ClickOnce](../deployment/how-to-specify-which-files-are-published-by-clickonce.md). Můžete také označit datové soubory pomocí Mage.exe. Další informace najdete v tématu [postupy: zahrnutí datového souboru do aplikace ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
### <a name="prerequisites-dialog-box"></a>Dialogové okno Požadavky  
 Toto dialogové okno určuje, které nezbytné součásti se instalují a jak jsou nainstalovány. Další informace najdete v tématu [postupy: instalace předpokladů s aplikací ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) a [dialogové okno požadavky](../ide/reference/prerequisites-dialog-box.md).  
  
### <a name="application-updates-dialog-box"></a>Dialogové okno aktualizace aplikace  
 Toto dialogové okno určuje, jak instalace aplikace by měla vyhledávat aktualizace. Další informace najdete v tématu [postupy: Správa aktualizací pro aplikaci ClickOnce](../deployment/how-to-manage-updates-for-a-clickonce-application.md).  
  
### <a name="publish-options-dialog-box"></a>Publikování dialogové okno Možnosti  
 Dialogové okno Možnosti publikování určuje možnosti nasazení vaší aplikace.  
  
|||  
|-|-|  
|[Postupy: Změna jazyka publikování pro aplikaci ClickOnce](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)|Popisuje, jak určit jazyk a jazykovou verzi tak, aby odpovídaly lokalizovanou verzi.|  
|[Postupy: Určení názvu úvodní nabídky pro aplikaci ClickOnce](../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)|Popisuje, jak změnit zobrazovaný název pro aplikaci ClickOnce.|  
|[Postupy: Určení obsahu pro technickou podporu](../deployment/how-to-specify-a-link-for-technical-support.md)|Popisuje, jak nastavit **adresu URL podpory** vlastnost, která identifikuje webové stránky nebo sdílené složky, kde mohou uživatelé získat informace o aplikaci.|  
|[Postupy: Určení adresy URL webu s podporou pro jednotlivé předpoklady v nasazení ClickOnce](../deployment/how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment.md)|Jsme vám ukázali, jak ručně upravit manifest aplikace zahrnout jednotlivých adres URL podpory pro každý požadavek.|  
|[Postupy: Určení stránky publikování pro aplikaci ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)|Popisuje, jak vygeneruje a publikuje výchozí webovou stránku (publish.htm) spolu s aplikace|  
|[Postupy: Přizpůsobení výchozí webové stránky ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)|Popisuje, jak přizpůsobit webovou stránku, která je automaticky generována a publikovat spolu s aplikace.|  
|[Postupy: Povolení funkce AutoStart pro instalace z média CD](../deployment/how-to-enable-autostart-for-cd-installations.md)|Popisuje postup povolení funkce AutoStart tak, aby aplikace ClickOnce se automaticky spustí, když je médium je vloženo.|  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Vytváření přidružení souborů pro aplikaci ClickOnce](../deployment/how-to-create-file-associations-for-a-clickonce-application.md)|Popisuje postup přidání podpory přípony názvu souboru do aplikace ClickOnce.|  
|[Postupy: Načtení informací řetězce dotazu do online aplikace ClickOnce](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)|Ukazuje, jak načíst parametry předané v adrese URL používá ke spuštění aplikace ClickOnce.|  
|[Postupy: Zákaz aktivace adresy URL aplikací ClickOnce pomocí Návrháře](../deployment/how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer.md)|Popisuje, jak přinutit uživatele a spusťte tak aplikaci z **Start** nabídky pomocí návrháře.|  
|[Postupy: Zákaz aktivace adresy URL aplikací ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)|Popisuje, jak přinutit uživatele a spusťte tak aplikaci z **Start** nabídky.|  
|[Návod: Stahování sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce pomocí Návrháře](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)|Vysvětluje, jak stáhnout aplikaci sestavení pouze při prvním použití aplikací pomocí návrháře.|  
|[Návod: Stahování sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Vysvětluje, jak stáhnout aplikaci sestavení pouze při prvním použití aplikace.|  
|[Návod: Stahování satelitních sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Popisuje, jak označit vaše satelitní sestavení jako volitelné a stáhnout pouze sestavení klientský počítač, musí mít nastavení aktuální jazykové verze.|  
|[Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)|Vysvětluje způsob používání nástrojů rozhraní .NET Framework pro nasazení aplikace ClickOnce.|  
|[Návod: Ruční nasazení aplikace ClickOnce, jež nevyžaduje opětovné podepsání a které zachovává údaje o poskytovateli](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)|Vysvětluje způsob používání nástrojů rozhraní .NET Framework pro nasazení aplikace ClickOnce bez opětovné podepisování manifestů.|  
|[NIB: Postupy: optimalizovat aplikace pro konkrétní typ procesoru](http://msdn.microsoft.com/en-us/294a75d2-4279-4b72-8298-2bea05be907a)|Vysvětluje, jak publikovat pro 64bitový procesor tak, že změníte **cílový procesor** nebo **Cílová platforma** vlastnosti ve vašem projektu.|  
|[Názorný postup: Zapnutí aplikace ClickOnce spouštět na více verzí rozhraní .NET Framework](http://msdn.microsoft.com/en-us/7f4383af-ed87-4853-b4d4-02a3967a5fd9)|Vysvětluje, jak povolit aplikace ClickOnce k instalaci a spuštění na více verzích rozhraní .NET Framework.|  
|[Návod: Vytvoření vlastního instalátoru pro aplikaci ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)|Vysvětluje, jak vytvořit vlastní instalační program pro instalaci aplikace ClickOnce.|  
|[Postupy: Publikování aplikace WPF s povolenými vizuálními styly](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)|Obsahuje podrobné pokyny pro řešení chyby, jež se zobrazí při pokusu o publikování aplikace WPF, která má povoleny vizuální styly.|  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)   
 [Referenční dokumentace technologie ClickOnce](../deployment/clickonce-reference.md)



