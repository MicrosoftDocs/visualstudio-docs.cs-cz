---
title: Šablony podpory webu | Microsoft Docs
description: Seznamte se se šablonami podpory webu. Šablony projektů a položek webu sady Visual Studio poskytují opakovaně použitelný a přizpůsobitelný webový projekt a zástupné procedury položek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a1bd391d13a6d650cb4d23ce78789a66ef50c2e3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898888"
---
# <a name="web-site-support-templates"></a>Šablony podpory webu
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Šablony projektů a položek webu poskytují opakovaně použitelný a přizpůsobitelný projekt webu a položky, které urychlují proces vývoje odebráním nutnosti vytvářet nové webové projekty a položky od začátku. Další informace o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] šablonách naleznete v tématu [vytváření šablon projektů a položek](../../ide/creating-project-and-item-templates.md).

## <a name="project-template-folder"></a>Složka šablony projektu
 Šablony webových projektů jsou obvykle nainstalovány na [*Instalační cesta sady Visual Studio*] \Common7\IDE\ProjectTemplates\Web \\ , každý v podsložce, která je pojmenována po webovém programovacím jazyce.

## <a name="project-file"></a>Soubor projektu
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Integrované vývojové prostředí (IDE) vyžaduje příponu souboru projektu jako způsob, jak namapovat šablonu na správný typ projektu. Vzhledem k tomu, že webové projekty nemají soubor projektu, je zástupná Přípona souboru projektu zaregistrována pro mapování šablony na typ projektu.

 V případě potřeby lze do šablony přidat řetězec s názvem jazyka, aby systém webového projektu mohl nastavit výchozí jazyk v dialogovém okně **Přidat novou položku** pro položky založené na šabloně. Řetězec musí být prvním řádkem souboru. Musí odpovídat názvu registrovanému v AddItemLanguageName v registraci modulu IntelliSense a názvu registrovanému v podtypu projektu (VsTemplate). Další informace najdete v tématu [atributy podpory](../../extensibility/internals/web-site-support-attributes.md)webu.

 Pokud řetězec není k dispozici, systém webového projektu se pokusí určit výchozí jazyk na základě atributu jazyka a přípon souborů stránek přidaných do webového projektu šablonou projektu.

## <a name="project-templates"></a>Šablony projektů
 Šablony projektů webu slouží k vytváření nových webů v reakci na příkaz **Nový web** v nabídce **soubor** . V současné době jsou podporovány tři typy projektů webu:

- Prázdné projekty webu

- Projekty webu

- Projekty webové služby

### <a name="empty-web-site-projects"></a>Prázdné projekty webu
 Tyto soubory vytvoří nový prázdný web v reakci na **prázdný** příkaz webu, který je k dispozici po zvolení možnosti **soubor**  >  **Nový web**:

- EmptyWeb. vstemplate

     Soubor šablony, který provede vytvoření nového prázdného webu.

- EmptyWeb. webproj

     Tento soubor je artefaktem systému šablony projektu. Splňuje odkaz na soubor projektu v souboru EmptyWeb. vstemplate.

### <a name="web-site-projects"></a>Projekty webu
 Tyto soubory vytvoří nový web jako odpověď na příkaz webu **ASP.NET** , který je k dispozici **po výběru položky**  >  **Nový web** webu:

- Default.aspx

     Výchozí domovská stránka nového webu. Atribut Language určuje jazyk CodeBehind a atribut CodeFile určuje závislý soubor, který obsahuje kód CodeBehind přidružený k této stránce.

- Default. aspx. *rozšíření*

     Závislý soubor, který obsahuje kód CodeBehind pro výchozí domovskou stránku. Jazyk CodeBehind Určuje *rozšíření* tohoto souboru.

- web.config

     Kořenový konfigurační soubor web.site

- WebApplication. vstemplate

     Soubor šablony, který určuje obsah řešení webu a vynucuje vytváření App_Data složky.

- WebApplication. webproj

     Tento soubor je artefaktem systému šablony projektu. Splňuje odkaz na soubor projektu v souboru WebApplication. vstemplate.

### <a name="web-service-projects"></a>Projekty webové služby
 Tyto soubory vytvoří nový web jako odpověď na příkaz **webové služby ASP.NET** , který je k dispozici po zvolení možnosti **soubor**  >  **Nový web**:

- Service. asmx

     Stránka HTML pro novou webovou službu Atribut Language určuje jazyk CodeBehind a atribut CodeBehind určuje závislý soubor, který obsahuje kód CodeBehind přidružený k této službě.

- Službám. *klapk*

     Závislý soubor, který implementuje třídu služby. Jazyk CodeBehind Určuje *rozšíření* tohoto souboru.

- web.config

- Kořenový konfigurační soubor web.site

- WebService. vstemplate

     Soubor šablony, který určuje obsah řešení webu a vynutí vytvoření App_Data a App_Code složky. Služba. soubor *rozšíření* se zkopíruje do složky App_Code.

- WebService. webproj

     Tento soubor je artefaktem systému šablony projektu. Splňuje odkaz na soubor projektu v souboru WebService. vstemplate.

## <a name="project-item-template-folder"></a>Složka šablony položky projektu
 Šablony webových projektů a položek jsou obvykle nainstalovány v [*Instalační cesta sady Visual Studio*] \Common7\IDE\ItemTemplates\Web \\ , každý v podsložce, která je pojmenována po svém webovém programovacím jazyce.

## <a name="project-item-templates"></a>Šablony položek projektu
 Šablony položek projektu webu slouží k přidání nových webových stránek do webu v reakci na příkaz **Přidat existující položku** . V současné době jsou podporovány tyto druhy webových stránek:

- Nová třída

- Nová stránka HTML

- Nový webový formulář

- Nová stránka předlohy

### <a name="new-class"></a>Nová třída
 Tato šablona vytvoří nový zdrojový soubor, který definuje prázdnou třídu v reakci na příkaz **Přidat novou třídu** .

- Deník. *klapk*

     Zdrojový soubor, který implementuje prázdnou třídu. Jazyk CodeBehind Určuje *rozšíření* tohoto souboru.

- Class. vstemplate

     Soubor šablony, který vytvoří zdrojový soubor a určí jeho obsah.

### <a name="new-html-page"></a>Nová stránka HTML
 Tato šablona vytvoří novou webovou stránku v reakci na příkaz **Přidat novou stránku HTML** .

- HTMLPage.htm

     Počáteční obsah webové stránky. K této webové stránce obvykle není přidružen žádný soubor závislý na CodeBehind. Chcete-li vytvořit inteligentní stránku s přidruženým souborem CodeBehind, použijte místo toho šablonu webového formuláře.

- HTMLPage. vstemplate

     Soubor šablony, který vytvoří webovou stránku a určí její obsah.

### <a name="new-webform"></a>Nový WebForm
 Tato šablona vytvoří novou inteligentní webovou stránku v reakci na příkaz **Přidat nový webový formulář** .

 Chcete-li vytvořit závislý zdrojový soubor codebehind, vyberte možnost **umístit kód do samostatného souboru**. V opačném případě se vytvoří jediná webová stránka, která má prázdný blok skriptování a žádné \<% Page %> direktivy pro připojení závislého souboru.

 Chcete-li vytvořit stránku obsahu pro vybranou stránku předlohy, vyberte možnost **Vybrat stránku předlohy**.

- WebForm. aspx

     Počáteční obsah webové stránky. K této webové stránce není přidružen žádný soubor závislý na CodeBehind.

- WebForm_cb. aspx

     Počáteční obsah webové stránky. Tato webová stránka má přidružený soubor závislý na CodeBehind.

- CodeBehind. *klapk*

     Závislý soubor, který implementuje třídu WebForm. Jazyk souboru codebehind určuje *příponu* tohoto souboru.

- ContentPage.aspx

     Počáteční obsah webové stránky jako stránka obsahu. Tato webová stránka nemá žádný přidružený závislý soubor s kódem.

- ContentPage_cb.aspx

     Počáteční obsah webové stránky jako stránka obsahu. Tato webová stránka má přidružený závislý soubor kódu.

- WebForm.vstemplate

     Soubor šablony, který určuje obsah nové webové stránky a jeho závislý soubor, pokud je k nějakému dojde.

### <a name="new-master-page"></a>Nová stránka předlohy
 Tato šablona vytvoří novou stránku předlohy v reakci na **příkaz Přidat novou stránku předlohy.**

 Pokud chcete vytvořit závislý zdrojový soubor kódu, vyberte **Umístit kód do samostatného souboru**. V opačném případě je vytvořena jedna webová stránka s prázdným blokem skriptování a bez direktiv pro \<% Page %> připojování závislého souboru.

- MasterPage.master

     Počáteční obsah stránky předlohy. Tato stránka předlohy nemá žádný přidružený závislý soubor kódu.

- MasterPage_cb.master

     Počáteční obsah stránky předlohy. Tato stránka předlohy má přidružený závislý soubor kódu.

- Codebehind. *rozšíření*

     Závislý soubor, který implementuje třídu stránky předlohy. Jazyk souboru codebehind určuje *příponu* tohoto souboru.

- MasterPage.vstemplate

     Soubor šablony, který určuje obsah nové stránky předlohy a jeho závislý soubor, pokud je k nějakému dojde.

## <a name="see-also"></a>Viz také
- [Podpora webu](../../extensibility/internals/web-site-support.md)
