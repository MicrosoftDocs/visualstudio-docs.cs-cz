---
title: Šablony podpory webu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eebacb3006826a90320cbc61edf7d56467e688ce
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760224"
---
# <a name="web-site-support-templates"></a>Šablony podpory webu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Šablony projektů a položek webu poskytují opakovaně použitelných a přizpůsobitelné webové stránky projektů a položek zástupné procedury, které zrychlení procesu vývoje tak, že odeberete potřebu vytvářet nové webových projektů a položek od začátku. Další informace o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] šablony, najdete v článku [vytváření projektů a šablon položek](../../ide/creating-project-and-item-templates.md).  
  
## <a name="project-template-folder"></a>Složka šablony projektu  
 Šablony webových projektů šablony jsou obvykle nainstalovány na [*Visual Studio Instalační cesta*] \Common7\IDE\ProjectTemplates\Web\\, každého do podsložky, která má stejný název webu programovací jazyk.  
  
## <a name="project-file"></a>Soubor projektu  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Integrované vývojové prostředí (IDE) vyžaduje příponu souboru projektu jako způsob, jak namapovat na správný projekt typu šablony. Protože webové projekty není nutné soubor projektu, je pro podporu tohoto zaregistrovaný .webproj fiktivní projektu souboru rozšíření.  
  
 Řetězec názvu jazykové Volitelně lze přidat do šablony pro povolení systém webového projektu, chcete-li nastavit výchozí jazyk **přidat novou položku** dialogové okno pro položky na základě šablony. Řetězec musí být první řádek souboru a musí odpovídat názvu zaregistrován AddItemLanguageName v registraci modulu technologie Intellisense a název projektu Subtype(VsTemplate) zaregistrován. Další informace najdete v tématu [atributy podpory webu](../../extensibility/internals/web-site-support-attributes.md).  
  
 Pokud řetězec není k dispozici, systém webového projektu se pokusí určit výchozí jazyk podle jazyka atribut a soubor rozšíření šablona projektu šablony přidal do projektu webové stránky.  
  
## <a name="project-templates"></a>Šablony projektů  
 Šablony projektů webu se používají k vytváření nových webů v reakci na **nový web** příkaz **souboru** nabídky. Aktuálně jsou podporovány tři typy projektů webu:  
  
-   Prázdný web webové projekty  
  
-   Webové projekty  
  
-   Projekty webových služeb  
  
### <a name="empty-web-site-projects"></a>Prázdný web webové projekty  
 Tyto soubory vytvořit nový prázdný web v reakci na **prázdný web** příkaz, který je k dispozici po odkazující na **nový web** na **souboru** nabídky:  
  
-   EmptyWeb.vstemplate  
  
     Soubor šablony, který provede vytvoření nového prázdného webu.  
  
-   EmptyWeb.webproj  
  
     Tento soubor je systém šablony projektu. Odkaz na soubor projektu v souboru EmptyWeb.vstemplate splňuje.  
  
### <a name="web-site-projects"></a>Webové projekty  
 Tyto soubory vytvořit novou webovou stránku v reakci na **Web ASP.NET s** příkaz, který je k dispozici po odkazující na **nový web** na **souboru** nabídky:  
  
-   Default.aspx  
  
     Výchozí domovskou stránku pro nový web. Atribut Language Určuje jazyk codebehind a určuje Atribut CodeFile závislý soubor obsahující kód codebehind přidružený k této stránce.  
  
-   Default.aspx. *rozšíření*  
  
     Závislý soubor, který obsahuje kód codebehind výchozí domovskou stránku. Určuje jazyk codebehind *rozšíření* tohoto souboru.  
  
-   web.config  
  
     Kořenové web.site konfigurační soubor.  
  
-   WebApplication.vstemplate  
  
     Soubor šablony, který zjistí obsah webu řešení a vynutí vytvoření souboru složce App_Data.  
  
-   WebApplication.webproj  
  
     Tento soubor je systém šablony projektu. Odkaz na soubor projektu v souboru WebApplication.vstemplate splňuje.  
  
### <a name="web-service-projects"></a>Projekty webových služeb  
 Tyto soubory vytvořit novou webovou stránku v reakci na **webová služba ASP.NET** příkazu, který je k dispozici po odkazující na **nový web** na **souboru** nabídky:  
  
-   Service.asmx  
  
     Na stránce HTML pro nové webové služby. Atribut Language Určuje jazyk codebehind a určuje atribut CodeBehind závislý soubor obsahující codebehind kód spojený s touto službou.  
  
-   Služba. *Rozšíření*  
  
     Závislý soubor, který implementuje třídu služby. Určuje jazyk codebehind *rozšíření* tohoto souboru.  
  
-   web.config  
  
-   Kořenové web.site konfigurační soubor.  
  
-   WebService.vstemplate  
  
     Soubor šablony, který zjistí obsah webu řešení a vynutí vytvoření složky App_Data a App_Code. Služba. *rozšíření* soubor je zkopírován do složky App_Code.  
  
-   WebService.webproj  
  
     Tento soubor je systém šablony projektu. Odkaz na soubor projektu v souboru WebService.vstemplate splňuje.  
  
## <a name="project-item-template-folder"></a>Složky šablony položky projektu  
 Webové šablony šablony položky projektu jsou obvykle nainstalován na [*Visual Studio Instalační cesta*] \Common7\IDE\ItemTemplates\Web\\, každou v podsložce s názvem po jeho web programovací jazyk.  
  
## <a name="project-item-templates"></a>Šablony položek projektu  
 Šablony položek projektu webové stránky se používají k přidání nové webové stránky pro webovou stránku v reakci **přidat existující položku** příkazu. Aktuálně jsou podporovány tyto druhy webové stránky:  
  
-   Nová třída  
  
-   Nová stránka HTML  
  
-   Nový webový formulář  
  
-   Nová stránka předlohy  
  
### <a name="new-class"></a>Nová třída  
 Tato šablona vytvoří nového zdrojového souboru, který definuje prázdnou třídu v reakci **přidejte novou třídu** příkazu.  
  
-   Třída. *Rozšíření*  
  
     Zdrojový soubor, který implementuje prázdnou třídu. Určuje jazyk codebehind *rozšíření* tohoto souboru.  
  
-   Class.vstemplate  
  
     Soubor šablony, která vytvoří zdrojový soubor a určuje jeho obsah.  
  
### <a name="new-html-page"></a>Nová stránka HTML  
 Tato šablona vytvoří novou webovou stránku v reakci **přidejte novou stránku HTML** příkazu.  
  
-   HTMLPage.htm  
  
     Výchozí obsah webové stránky. Tato webová stránka obvykle nemá žádný přidružený codebehind závislý soubor. Vytvořit stránku inteligentní souborem přidružené codebehind, použijte šablonu Webový formulář.  
  
-   HTMLPage.vstemplate  
  
     Soubor šablony, která vytvoří webovou stránku a určuje jeho obsah.  
  
### <a name="new-webform"></a>Nový webový formulář  
 Tato šablona vytvoří novou inteligentní webovou stránku v reakci **přidat nový webový formulář** příkazu.  
  
 Chcete-li vytvořit závislé codebehind zdrojový soubor, vyberte **umístěte kód v samostatném souboru**. Jediné webové stránky v opačném případě se vytvoří, který má prázdný skriptovací bloku a ne \<stránky % > direktivy propojení závislého souboru.  
  
 Chcete-li vytvořit stránku obsahu pro vybranou stránku předlohy, vyberte **vyberte stránku předlohy**.  
  
-   WebForm.aspx  
  
     Výchozí obsah webové stránky. Tato webová stránka nemá žádný přidružený codebehind závislý soubor.  
  
-   WebForm_cb.aspx  
  
     Výchozí obsah webové stránky. Tato webová stránka má závislý soubor přidružené codebehind.  
  
-   CodeBehind. *Rozšíření*  
  
     Závislý soubor, který implementuje třídu webového formuláře. Určuje jazyk codebehind *rozšíření* tohoto souboru.  
  
-   ContentPage.aspx  
  
     Výchozí obsah webové stránky jako stránku obsahu. Tato webová stránka nemá žádný přidružený codebehind závislý soubor.  
  
-   ContentPage_cb.aspx  
  
     Výchozí obsah webové stránky jako stránku obsahu. Tato webová stránka má závislý soubor přidružené codebehind.  
  
-   WebForm.vstemplate  
  
     Soubor šablony, která určuje obsah nové webové stránky a jeho závislých souborů, pokud existuje.  
  
### <a name="new-master-page"></a>Nová stránka předlohy  
 Tato šablona vytvoří novou stránku předlohy v reakci **přidejte novou stránku předlohy** příkazu.  
  
 Chcete-li vytvořit závislé codebehind zdrojový soubor, vyberte **umístěte kód v samostatném souboru**. Jediné webové stránky v opačném případě se vytvoří, který má prázdný skriptovací bloku a ne \<stránky % > direktivy propojení závislého souboru.  
  
-   MasterPage.master  
  
     Výchozí obsah stránky předlohy. Tato stránka předlohy nemá žádný soubor závislé přidružené codebehind.  
  
-   MasterPage_cb.master  
  
     Výchozí obsah stránky předlohy. Tato hlavní stránka má závislý soubor přidružené codebehind.  
  
-   CodeBehind. *rozšíření*  
  
     Závislý soubor, který implementuje třídu stránky předlohy. Určuje jazyk codebehind *rozšíření* tohoto souboru.  
  
-   MasterPage.vstemplate  
  
     Soubor šablony, která určuje obsah nové stránky předlohy a jeho závislých souborů, pokud existuje.  
  
## <a name="see-also"></a>Viz také  
 [Podpora webu](../../extensibility/internals/web-site-support.md)

