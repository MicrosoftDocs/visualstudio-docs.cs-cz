---
title: Šablony podpory webu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e3c139ae6f2f9ec618e6382a1551a9e35eee7ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703457"
---
# <a name="web-site-support-templates"></a>Šablony podpory webu
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Šablony projektů a položek webu poskytují opakovaně použitelné a přizpůsobitelné zástupné položky webových stránek a položek, které urychlují proces vývoje tím, že odstraňují potřebu vytvářet nové projekty a položky webu od začátku. Další informace [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o šablonách naleznete v [tématu Vytváření šablon projektů a položek](../../ide/creating-project-and-item-templates.md).

## <a name="project-template-folder"></a>Složka šablony projektu
 Šablony webových projektů jsou obvykle nainstalovány v*aplikaci*[ Instalační cesta sady\\Visual Studio ]\Common7\IDE\ProjectTemplates\Web , každá v podsložce pojmenované po webovém programovacím jazyce.

## <a name="project-file"></a>Soubor projektu
 Integrované [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vývojové prostředí (IDE) vyžaduje příponu souboru projektu jako způsob, jak namapovat šablonu na správný typ projektu. Vzhledem k tomu, že webové projekty nemají soubor projektu, je zaregistrována fiktivní přípona souboru projektu .webproj, která má namapovat šablonu na typ projektu.

 Volitelně lze do šablony přidat řetězec názvu jazyka, aby systém webového projektu mohl nastavit výchozí jazyk v dialogovém okně **Přidat novou položku** pro položky založené na šabloně. Řetězec musí být prvním řádkem souboru. Musí odpovídat jak názvu registrovanému v části AddItemLanguageName v registraci modulu IntelliSense, tak názvu registrovanému podtypem projektu(VsTemplate). Další informace naleznete v [tématu Atributy podpory webu](../../extensibility/internals/web-site-support-attributes.md).

 Pokud řetězec není k dispozici, systém webového projektu se pokusí určit výchozí jazyk na základě atributu Language a přípon souborů stránek přidaných do webového projektu šablonou projektu.

## <a name="project-templates"></a>Šablony projektů
 Šablony projektů webu se používají k vytváření nových webových serverů v reakci na příkaz **Nový web** v nabídce **Soubor.** V současné době jsou podporovány tři typy webových projektů:

- Prázdné projekty webu

- Projekty webových stránek

- Projekty webových služeb

### <a name="empty-web-site-projects"></a>Prázdné projekty webu
 Tyto soubory vytvoří nový prázdný web v reakci na příkaz **Prázdný web,** který je k dispozici po výběru **možnosti Nový** > **soubor :**

- Šablona EmptyWeb.vs

     Soubor šablony, který řídí vytvoření nového prázdného webu.

- PrázdnýWeb.webproj

     Tento soubor je artefakt systému šablony projektu. Splňuje odkaz na soubor projektu v souboru EmptyWeb.vstemplate.

### <a name="web-site-projects"></a>Projekty webu
 Tyto soubory vytvoří nový web v reakci na příkaz **ASP.NET webu,** který je k dispozici po **výběru možnosti Nový** > **soubor :**

- Default.aspx

     Výchozí domovská stránka nového webu. Atribut Language určuje kód za jazykem a atribut CodeFile určuje závislý soubor, který obsahuje kód přidružený k této stránce.

- Default.aspx. *rozšíření*

     Závislý soubor, který obsahuje kód za kódem pro výchozí domovskou stránku. Kód za jazykurčuje *rozšíření* tohoto souboru.

- Souboru web.config

     Kořenový konfigurační soubor web.webu.

- WebApplication.vstemplate

     Soubor šablony, který určuje obsah řešení webu a vynutí vytvoření App_Data složky.

- WebApplication.webproj

     Tento soubor je artefakt systému šablony projektu. Splňuje odkaz na soubor projektu v souboru WebApplication.vstemplate.

### <a name="web-service-projects"></a>Projekty webových služeb
 Tyto soubory vytvoří nový web v reakci na příkaz **ASP.NET Web Service,** který je k dispozici po výběru **možnosti Nový** > **soubor :**

- Service.asmx

     Stránka HTML pro novou webovou službu. Atribut Language určuje kód za jazykem a atribut CodeBehind určuje závislý soubor, který obsahuje kód přidružený k této službě.

- Služby. *Rozšíření*

     Závislý soubor, který implementuje třídu služby. Kód za jazykurčuje *rozšíření* tohoto souboru.

- Souboru web.config

- Kořenový konfigurační soubor web.webu.

- Šablona WebService.vstemplate

     Soubor šablony, který určuje obsah řešení webu a vynutí vytvoření App_Data a App_Code složky. Služba. *přímkový* soubor zkopírován do složky App_Code.

- WebService.webproj

     Tento soubor je artefakt systému šablony projektu. Splňuje odkaz na soubor projektu v souboru WebService.vstemplate.

## <a name="project-item-template-folder"></a>Složka šablony položky projektu
 Šablony položek webového projektu jsou obvykle nainstalovány v*aplikaci*[ Instalační cesta sady\\Visual Studio ]\Common7\IDE\ItemTemplates\Web , každá v podsložce, která je pojmenována po svém webovém programovacím jazyce.

## <a name="project-item-templates"></a>Šablony položek projektu
 Šablony položek projektu webu se používají k přidání nových webových stránek na web jako odpověď na příkaz **Přidat existující položku.** Tyto typy webových stránek jsou aktuálně podporovány:

- Nová třída

- Nová stránka HTML

- Nový webový formulář

- Nová stránka předlohy

### <a name="new-class"></a>Nová třída
 Tato šablona vytvoří nový zdrojový soubor, který definuje prázdnou třídu v reakci na příkaz **Přidat novou třídu.**

- Třída. *Rozšíření*

     Zdrojový soubor, který implementuje prázdnou třídu. Kód za jazykurčuje *rozšíření* tohoto souboru.

- Třída.vsšablona

     Soubor šablony, který vytvoří zdrojový soubor a určuje jeho obsah.

### <a name="new-html-page"></a>Nová stránka HTML
 Tato šablona vytvoří novou webovou stránku v reakci na příkaz **Přidat novou stránku HTML.**

- SOUBOR HTMLPage.htm

     Počáteční obsah webové stránky. Tato webová stránka obvykle nemá žádný přidružený kód za závislým souborem. Chcete-li vytvořit inteligentní stránku s přidruženým souborem s kódem, použijte místo toho šablonu webového formuláře.

- Šablona HTMLPage.vstemplate

     Soubor šablony, který vytvoří webovou stránku a určí její obsah.

### <a name="new-webform"></a>Nový webový formulář
 Tato šablona vytvoří novou inteligentní webovou stránku v reakci na příkaz **Přidat nový webový formulář.**

 Chcete-li vytvořit závislý kód za zdrojovým souborem, vyberte **Umístit kód do samostatného souboru**. V opačném případě je vytvořena jedna webová stránka, \<která má prázdný blok skriptování a žádné % stránky %> direktivy připojit závislý soubor.

 Chcete-li vytvořit stránku obsahu pro vybranou stránku předlohy, vyberte **vybrat stránku předlohy**.

- WebForm.aspx

     Počáteční obsah webové stránky. Tato webová stránka nemá žádný přidružený kód za závislým souborem.

- WebForm_cb.aspx

     Počáteční obsah webové stránky. Tato webová stránka má přidružený kód za závislým souborem.

- Codebehind. *Rozšíření*

     Závislý soubor, který implementuje třídu webform. Kód za jazykurčuje *rozšíření* tohoto souboru.

- ContentPage.aspx

     Počáteční obsah webové stránky jako stránky obsahu. Tato webová stránka nemá žádný přidružený kód za závislým souborem.

- ContentPage_cb.aspx

     Počáteční obsah webové stránky jako stránky obsahu. Tato webová stránka má přidružený kód za závislým souborem.

- Šablona WebForm.vstemplate

     Soubor šablony, který určuje obsah nové webové stránky a její závislý soubor, pokud existuje.

### <a name="new-master-page"></a>Nová stránka předlohy
 Tato šablona vytvoří novou stránku předlohy v reakci na příkaz **Přidat novou stránku předlohy.**

 Chcete-li vytvořit závislý kód za zdrojovým souborem, vyberte **Umístit kód do samostatného souboru**. V opačném případě je vytvořena jedna webová stránka, která má prázdný blok skriptování a žádné \<% stránky %> direktivy připojit závislý soubor.

- MasterPage.master

     Počáteční obsah stránky předlohy. Tato stránka předlohy nemá žádný přidružený kód za závislým souborem.

- MasterPage_cb.master

     Počáteční obsah stránky předlohy. Tato stránka předlohy má přidružený kód za závislým souborem.

- Codebehind. *rozšíření*

     Závislý soubor, který implementuje třídu vzorové stránky. Kód za jazykurčuje *rozšíření* tohoto souboru.

- Šablona MasterPage.vstemplate

     Soubor šablony, který určuje obsah nové stránky předlohy a její závislý soubor, pokud existuje.

## <a name="see-also"></a>Viz také
- [Podpora webu](../../extensibility/internals/web-site-support.md)
