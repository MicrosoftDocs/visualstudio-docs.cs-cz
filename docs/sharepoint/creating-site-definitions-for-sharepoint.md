---
title: Vytváření definic webu pro službu SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0e43cfa7c9fa78722639053c572280cbaad912bf
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36325339"
---
# <a name="create-site-definitions-for-sharepoint"></a>Vytvoření definic webu pro službu SharePoint
  Do projektu definice webu služby SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] umožňuje vytvářet *lokalita definice*, který slouží jako základ pro nový web služby SharePoint. Tyto definice nejen určit vzhled a chování webu služby SharePoint, ale jeho výchozí obsah a funkce. V definici lze umístit předkonfigurované seznamy, typy obsahu, přijímače událostí, obrázky a další položky. SharePoint zahrnuje některé definice webů, jako je například BLOG, např. Při vytvoření webu na základě definice lokality BLOG lokalita obsahuje seznamy, webové části a další položky, které web blogu vyžaduje.  
  
 Další informace o definicích lokality najdete v tématu [šablony webů a definice](http://go.microsoft.com/fwlink/?LinkId=179134).  
  
## <a name="site-definition-projects"></a>Projekty definice lokality
 Lokality definice projekty v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zadejte pouze základní soubory, které potřebuje webu SharePoint; neposkytují žádné výchozí funkce. Je třeba přidat soubory a obsah poskytuje funkce, které chcete. Webu můžete vytvořit ručně pomocí vytvoření a přidání soubory, které potřebujete.  
  
## <a name="feature-stapling"></a>Funkce – sešívání
 Jednou z výhod vytváření definic webu v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] je, že automaticky použijí *– sešívání funkce*. Funkce sešívání funkce připojí k definici lokality místo vkládání jejich funkci v definici lokality sám sebe. To umožňuje přidat funkci k žádné lokalitě vytvořili pomocí definice webu bez úpravy původní definice webu. Další informace najdete v tématu [– sešívání funkce](http://go.microsoft.com/fwlink/?LinkID=119283).  
  
## <a name="site-definition-project-components"></a>Součásti projektu definice webu
 Při vytváření definice řešení lokality následující výchozí soubory jsou přidány do jeho **SiteDefinition** uzlu.  
  
|Název souboru|Popis|  
|---------------|-----------------|  
|*default.aspx*|ASPX výchozí domovskou stránku pro nový web služby SharePoint.|  
|*onet.XML*|Určuje konfiguraci nové lokality, komponenty lokality definice šablony a výchozí chování. Tato nastavení může patřit atributy jako typy obsahu, které jsou povolené, zobrazení seznamu výchozí šablony dokumentů a webovými částmi součástí webu. Ve výchozím nastavení `Modules` část obsahuje soubory, které mají být přidány do web služby SharePoint a jejich konfiguraci.|  
|*webtemp_\<SiteDefinitionName > .xml*|Určuje definici konfigurace lokality, které se zobrazí v **výběr šablony** části **nový web služby SharePoint** stránky.|  
  
 Ve výchozím nastavení, všechny definice lokality jsou uloženy v  *\<jednotka: > \Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates* složky. Každý definice lokality má svou vlastní podsložky.  
  
## <a name="related-topics"></a>Související témata
  
|Název|Popis|  
|-----------|-----------------|  
|[Návod: Vytvoření základního projektu definice webu](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Vás provede procesem vytvoření základního projektu definice webu v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Postupy: vytvoření vlastní stránky definice a konfigurace](http://go.microsoft.com/fwlink/?LinkId=183309)|Popisuje, jak vytvořit definici vlastní stránky ve službě SharePoint tak, že existující definice lokality a potom můžete tuto kopii upravit.|  
|[*WebTemp.xml*](http://go.microsoft.com/fwlink/?LinkId=183310)|Popisuje původní soubor, který určuje k dispozici v lokalitě definice **výběr šablony** části **nový web služby SharePoint** stránky.|  
|[Lokalizace řešení služby SharePoint](../sharepoint/localizing-sharepoint-solutions.md)|Popisuje, jak připravit vaše řešení služby SharePoint pro globální použití.|  
|[Vytvoření webové části pro službu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Popisuje, jak můžete vytvořit částí stránku služby SharePoint, které mohou uživatelé změnit.|  
|[Vytváření opakovaně použitelných ovládacích prvků pro webové části nebo stránky aplikací](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Popisuje, jak můžete vytvořit opakovaně použitelných ovládacích prvků, které běží v stránky aplikací a webové části.|  
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|Popisuje, jak používat návrháře, které se zobrazí po otevření webové stránky ve vašem projektu.|  
|[Přehled technologie ASP.NET Web Pages](http://go.microsoft.com/fwlink/?LinkId=178726)|Poskytuje obecné informace o struktuře [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] webové stránky, jak jsou zpracovávány pomocí [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]a jak [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] stránky zobrazí kód, který splňuje standardy XHTML.|  
|[Syntaxe webové stránky ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178727)|Popisuje elementy značek, které tvoří stránku ASP.NET.|  
|[Programování webových stránek ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178728)|Poskytuje informace o tom, jak vytvořit obslužné rutiny událostí v [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] stránky a jak pracovat s klientského skriptu.|  
|[Programování v služby Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=178729)|Popisuje způsob použití modelu spravovaného objektu, která je součástí [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)].|  
  
## <a name="see-also"></a>Viz také:
 [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
 
