---
title: Vytváření definic webů pro SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0f1a512218c3c1b7af179cfaba3e231a90941fe0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015065"
---
# <a name="create-site-definitions-for-sharepoint"></a>Vytvořit definice webu pro SharePoint
  Projekt definice webu služby SharePoint v aplikaci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] umožňuje vytvořit *definici webu*, která slouží jako základ pro nový web služby SharePoint. Tyto definice nejen určují vzhled a chování webu služby SharePoint, ale také jeho výchozí obsah a funkce. V definici můžete vložit předem konfigurované seznamy, typy obsahu, přijímače událostí, obrázky a další položky. SharePoint obsahuje některé definice webů, například BLOG. Když vytvoříte lokalitu na základě definice webu blogu, lokalita obsahuje seznamy, webové části a další položky, které vyžaduje blogovací Web.

 Další informace o definicích lokalit najdete v tématu [šablony a definice webů](/previous-versions/office/developer/sharepoint-2010/ms434313(v=office.14)).

## <a name="site-definition-projects"></a>Projekty definice webu
 Projekty definice webu v nástroji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] poskytují pouze základní soubory, které web služby SharePoint potřebuje. neposkytují žádné výchozí funkce. Je nutné přidat soubory a obsah, abyste poskytovali požadované funkce. Lokalitu můžete vytvořit ručně tak, že vytvoříte a přidáte soubory, které potřebujete.

## <a name="feature-stapling"></a>Připojování funkcí
 Jedna z výhod vytváření definic webů v nástroji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] je, že automaticky používá připojení *funkcí*. Připojování funkcí připojí funkci k definici webu místo vložení jeho funkcí do samotné definice webu. To umožňuje přidat funkci na libovolný web vytvořený pomocí definice webu bez změny původní definice webu. Další informace najdete v tématu věnovaném [připojování funkcí](/previous-versions/office/developer/sharepoint-2007/bb861862(v=office.12)).

## <a name="site-definition-project-components"></a>Součásti projektu definice webu
 Při vytváření řešení definice webu jsou do svého uzlu **sitedefinition** přidány následující výchozí soubory.

|Název souboru|Popis|
|---------------|-----------------|
|*Default. aspx*|Výchozí domovská stránka ASPX pro nový web služby SharePoint.|
|*onet.xml*|Určuje konfiguraci nového webu, součástí šablony definice webu a výchozího chování. Tato nastavení můžou zahrnovat atributy, jako jsou povolené typy obsahu, které jsou povolené, výchozí zobrazení seznamu, soubory šablon dokumentů a webové části, které jsou součástí tohoto webu. Ve výchozím nastavení `Modules` obsahuje oddíl soubory, které se mají přidat do sharepointového webu a jak se konfigurují.|
|*webtemp_ \<SiteDefinitionName> . XML*|Určuje konfigurace definic webů, které se zobrazí v části **Výběr šablony** na **nové stránce webu SharePoint** .|

 Ve výchozím nastavení se všechny definice lokalit ukládají do složky * \<drive:> \Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates* . Každá definice webu má svou vlastní podsložku.

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Návod: Vytvoření základního projektu definice webu](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Provede vás podrobným vytvořením základního projektu definice webu v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|
|[Postupy: Vytvoření vlastní definice a konfigurace webu](/previous-versions/office/developer/sharepoint-2010/ms454677(v=office.14))|Popisuje, jak vytvořit vlastní definici webu ve službě SharePoint zkopírováním existující definice webu a následnou úpravou kopie.|
|[*WebTemp.xml*](/previous-versions/office/developer/sharepoint-2010/ms447717(v=office.14))|Popisuje původní soubor, který určuje definice webů, které jsou k dispozici v části **Výběr šablony** na **nové stránce webu služby SharePoint** .|
|[Lokalizace řešení služby SharePoint](../sharepoint/localizing-sharepoint-solutions.md)|Popisuje, jak připravit řešení služby SharePoint pro globální použití.|
|[Vytváření webových částí pro službu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Popisuje, jak lze vytvořit části stránky služby SharePoint, které mohou uživatelé upravovat.|
|[Vytváření opakovaně použitelných ovládacích prvků pro webové části nebo stránky aplikací](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Popisuje, jak lze vytvořit opakovaně použitelné ovládací prvky, které jsou spouštěny na stránkách aplikace a Webové části.|
|[Visual Web Developer](/previous-versions/visualstudio/visual-studio-2010/ms178093(v=vs.100))|Popisuje způsob použití návrháře, který se zobrazí při otevření webové stránky v projektu.|
|[ASP.NET – přehled webových stránek](/previous-versions/aspnet/428509ah(v=vs.100))|Poskytuje obecné informace o struktuře [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] webových stránek, způsobu, jakým jsou zpracovávány stránky [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] , a způsobu, jakým [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] stránky zobrazují značky, které vyhovují standardům XHTML.|
|[Syntaxe webové stránky ASP.NET](/previous-versions/aspnet/k33801s3(v=vs.100))|Popisuje prvky značek, které tvoří ASP.NET stránku.|
|[Programování webových stránek ASP.NET](/previous-versions/aspnet/0yt4zca8(v=vs.100))|Poskytuje informace o tom, jak vytvořit obslužné rutiny událostí na [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] stránkách a jak pracovat s klientským skriptem.|
|[Programování ve službě Windows SharePoint Services](/previous-versions/office/developer/sharepoint-services/ms430674(v=office.12))|Popisuje způsob použití spravovaného objektového modelu, který je k dispozici v [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] .|

## <a name="see-also"></a>Viz také
- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)
