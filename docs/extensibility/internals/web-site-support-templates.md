---
title: Webový server podporují šablony | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af8e0d845157b475e4a5527443f55286828023cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31147125"
---
# <a name="web-site-support-templates"></a>Podpora šablony webových serverů
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Šablony projektů a položek webu poskytují opakovaně použitelný a přizpůsobitelné webové stránky projektů a položek zástupnými procedurami, které urychlit proces vývoje odebráním potřebu vytvářet nové webové projekty a položky od začátku. Další informace o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] šablony, viz [vytváření projektů a šablon položek](../../ide/creating-project-and-item-templates.md).

## <a name="project-template-folder"></a>Složka šablon projektu
 Šablony webových projektů jsou obvykle nainstalovány na [*Visual Studio Instalační cesta*] \Common7\IDE\ProjectTemplates\Web\\, každou v podsložce s názvem po webu programovací jazyk.

## <a name="project-file"></a>Soubor projektu
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Integrované vývojové prostředí (IDE) vyžaduje příponu souboru projektu jako způsob, jak namapovat šablonu typu správný projekt. Protože webové projekty nemají soubor projektu, .webproj fiktivní projektu soubor rozšíření je zaregistrován k mapování šablony na typ projektu.

 Volitelně lze přidat řetězec názvu jazyk v šabloně, aby systém webového projektu nastavit výchozí jazyk v **přidat novou položku** dialogové okno pro položky založený na šabloně. První řádek souboru musí být řetězec. Musí se shodovat název v rámci AddItemLanguageName zaregistrována v registraci modulu IntelliSense a název je registrovaná pod Subtype(VsTemplate) projektu. Další informace najdete v tématu [webu podpory atributy](../../extensibility/internals/web-site-support-attributes.md).

 Pokud řetězec není dostupná, systému webového projektu se pokusí určit výchozí jazyk podle jazyková rozšíření atribut a soubor stránek v šabloně projektů přidal k webovému projektu.

## <a name="project-templates"></a>Šablony projektů
 Šablony projektů webu se používají k vytváření nových webů v reakci na **nový web** příkaz na **souboru** nabídky. Aktuálně jsou podporovány tři typy projektů webové stránky:

-   Prázdné projekty

-   Webové projekty

-   Webové projekty služby

### <a name="empty-web-site-projects"></a>Prázdné projekty
 Tyto soubory vytvořit nový prázdný web v reakci **prázdný web** příkaz, který je k dispozici po výběru **soubor** > **nový web**:

-   EmptyWeb.vstemplate

     Soubor šablony, který provede vytvoření nové prázdné webové stránky.

-   EmptyWeb.webproj

     Tento soubor je artefakt systému šablona projektu. Odkaz na soubor projektu v souboru EmptyWeb.vstemplate splňuje.

### <a name="web-site-projects"></a>Webové projekty
 Tyto soubory vytvořit nový web v reakci **webové stránky ASP.NET** příkaz, který je k dispozici po výběru **soubor** > **nový web**:

-   Default.aspx

     Výchozí domovskou stránku pro nový web. Atribut Language Určuje jazyk codebehind a atribut CodeFile určuje závislý soubor, který obsahuje kód codebehind přidružené k této stránce.

-   Default.aspx. *rozšíření*

     Závislý soubor, který obsahuje kód codebehind pro výchozí domovskou stránku. Určuje jazyk codebehind *rozšíření* tohoto souboru.

-   web.config

     Kořenové web.site konfigurační soubor.

-   WebApplication.vstemplate

     Soubor šablony, která určuje obsah webu řešení a vynutí vytvoření souboru složce App_Data.

-   WebApplication.webproj

     Tento soubor je artefakt systému šablona projektu. Odkaz na soubor projektu v souboru WebApplication.vstemplate splňuje.

### <a name="web-service-projects"></a>Webové projekty služby
 Tyto soubory vytvořit nový web v reakci **webovou službu ASP.NET** příkaz, který je k dispozici po výběru **soubor** > **nový web**:

-   Service.asmx

     Na stránce HTML pro novou webovou službu. Atribut Language Určuje jazyk codebehind a atribut CodeBehind určuje závislý soubor, který obsahuje kód codebehind přidruženého k této službě.

-   Služba. *Rozšíření*

     Závislý soubor, který implementuje třídu služby. Určuje jazyk codebehind *rozšíření* tohoto souboru.

-   web.config

-   Kořenové web.site konfigurační soubor.

-   WebService.vstemplate

     Soubor šablony, která určuje obsah webu řešení a vynutí vytvoření souboru složky App_Data a App_Code. Služba. *rozšíření* soubor zkopírován do složky App_Code.

-   WebService.webproj

     Tento soubor je artefakt systému šablona projektu. Odkaz na soubor projektu v souboru WebService.vstemplate splňuje.

## <a name="project-item-template-folder"></a>Složky šablony položek projektu
 Šablony položek projektů webové jsou obvykle nainstalovány v [*Visual Studio Instalační cesta*] \Common7\IDE\ItemTemplates\Web\\, každou v podsložce s názvem po jeho webové programovací jazyk.

## <a name="project-item-templates"></a>Šablony položek projektu
 Šablony položek projektu webu slouží k přidání nové webové stránky na web v reakci **přidat existující položku** příkaz. Tyto typy webových stránek se aktuálně podporují:

-   Nová třída

-   Nová stránka HTML

-   Nový webový formulář

-   Nové stránky předlohy

### <a name="new-class"></a>Nová třída
 Tato šablona vytvoří nové zdrojového souboru, který definuje třídu prázdný v reakci **přidejte novou třídu** příkaz.

-   Třída. *Rozšíření*

     Zdrojový soubor, který implementuje třídu prázdný. Určuje jazyk codebehind *rozšíření* tohoto souboru.

-   Class.vstemplate

     Soubor šablony, které vytváří zdrojový soubor a určuje jeho obsah.

### <a name="new-html-page"></a>Nová stránka HTML
 Tato šablona umožňuje vytvořit novou webovou stránku v reakci **přidat novou stránku HTML** příkaz.

-   HTMLPage.htm

     Počáteční obsah webové stránky. Tato webová stránka má obvykle žádné přidružené codebehind závislý soubor. Vytvoření inteligentního stránky se souborem přidružené codebehind, použijte šablonu Webový formulář.

-   HTMLPage.vstemplate

     Soubor šablony, který vytvoří webovou stránku a určuje jeho obsah.

### <a name="new-webform"></a>Nový webový formulář
 Tato šablona vytvoří novou inteligentní webovou stránku v reakci **přidat nový webový formulář** příkaz.

 Chcete-li vytvořit závislé codebehind zdrojového souboru, vyberte **umístit kód do samostatného souboru**. Jednu webovou stránku, jinak se vytvoří bloku prázdný skriptování a ne \<% stránky % > direktivy spojit závislý soubor.

 Chcete-li vytvořit stránku obsahu pro vybrané stránky předlohy, vyberte **vyberte stránku předlohy**.

-   WebForm.aspx

     Počáteční obsah webové stránky. Tato webová stránka nemá žádné přidružené codebehind závislý soubor.

-   WebForm_cb.aspx

     Počáteční obsah webové stránky. Tato webová stránka obsahuje závislý soubor přidružené codebehind.

-   CodeBehind. *Rozšíření*

     Závislý soubor, který implementuje třídu webového formuláře. Určuje jazyk codebehind *rozšíření* tohoto souboru.

-   ContentPage.aspx

     Počáteční obsah webové stránky jako stránky obsahu. Tato webová stránka nemá žádné přidružené codebehind závislý soubor.

-   ContentPage_cb.aspx

     Počáteční obsah webové stránky jako stránky obsahu. Tato webová stránka obsahuje závislý soubor přidružené codebehind.

-   WebForm.vstemplate

     Soubor šablony, který určuje obsah novou webovou stránku a jeho závislých souborů, pokud existuje.

### <a name="new-master-page"></a>Nová stránka předlohy
 Tato šablona vytvoří novou stránku předlohy v reakci **přidat nová stránka předlohy** příkaz.

 Chcete-li vytvořit závislé codebehind zdrojového souboru, vyberte **umístit kód do samostatného souboru**. Jinak, jedné webové stránky je vytvořen, který obsahuje blok prázdný skriptování a neexistuje žádný \<% stránky % > direktivy spojit závislý soubor.

-   MasterPage.master

     Počáteční obsah stránky předlohy. Tato stránka předlohy nemá žádné přidružené codebehind závislý soubor.

-   MasterPage_cb.master

     Počáteční obsah stránky předlohy. Tato stránka předlohy má závislý soubor přidružené codebehind.

-   CodeBehind. *rozšíření*

     Závislý soubor, který implementuje třídu stránky předlohy. Určuje jazyk codebehind *rozšíření* tohoto souboru.

-   MasterPage.vstemplate

     Soubor šablony, který určuje obsah nové stránky předlohy a jeho závislých souborů, pokud existuje.

## <a name="see-also"></a>Viz také
 [Podpora webu](../../extensibility/internals/web-site-support.md)