---
title: Sloučení XML do funkce a balíku manifestů | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d3101245d720e9fdd1c4923ea03acd5b2d4db816
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120268"
---
# <a name="merge-xml-in-feature-and-package-manifests"></a>Sloučení XML do manifestů funkce a balíku
  Funkce a balíčky jsou definovány [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] manifest soubory. Tyto zabalené manifesty představují kombinaci data vygenerovaná ze návrháři a vlastní [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] zadané v šabloně manifestu uživateli. Během balení [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] slučuje vlastní [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] příkazy s zadaný Návrhář [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] na formuláři zabalené [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] souboru manifestu. Podobným elementům s výjimky uvedené dále v sloučení výjimky jsou sloučeny předejdete [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] chyby ověření po nasazení soubory do služby SharePoint, a aby manifest soubory menší a efektivnější.  
  
## <a name="modify-the-manifests"></a>Upravit manifestů
 Souborů v manifestu balíčku nemohou upravovat přímo, dokud zakážete návrháři funkce nebo balíčku. Však můžete ručně přidat vlastní [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementy do manifestu šablony buď prostřednictvím funkce a balíku Designer nebo [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] editor. Další informace najdete v tématu [postupy: přizpůsobení funkce služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md) a [postupy: přizpůsobení balíčku řešení služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
## <a name="feature-and-package-manifest-merge-process"></a>Funkce a balíku manifest proces sloučení
 Při kombinování vlastní elementy společně s Zadaný návrhář elementy [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] používá následující proces. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kontroluje, zda má každý element jedinečnou hodnotu klíče. Pokud element má žádná hodnota jedinečné klíče, připojí se k zabalené souboru manifestu. Podobně nelze sloučit prvky, které mít několik klíčů. Proto se připojují k souboru manifestu.  
  
 Pokud element má jedinečný klíč, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] porovnává hodnoty designer a vlastní klíče. Pokud se hodnoty shodují, sloučení do jedné hodnoty. Pokud se hodnoty liší, budou zahozeny návrháře hodnota klíče a používá vlastní hodnota klíče. Sloučena jsou rovněž kolekce. Například pokud generované Návrhář [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] a vlastní [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] současně obsahovat kolekci sestavení, zabalené manifest obsahuje pouze jednu kolekci sestavení.  
  
## <a name="merge-exceptions"></a>Merge – výjimky
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Sloučí většina Návrhář [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementy společně s podobnou vlastní [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] prvky, pokud mají jeden jedinečné identifikační atribut. Ale některé prvky nedostatku jedinečný identifikátor požadované pro [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] sloučení. Tyto prvky se označují jako *sloučení výjimky*. V těchto případech [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nesloučí vlastní [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementy společně s zadaný Návrhář [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementů, ale místo toho je připojí k zabalené souboru manifestu.  
  
 Následuje seznam sloučení výjimky pro funkce a balíku [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] manifest soubory.  
  
|Návrhář|XML Element|  
|--------------|-----------------|  
|Funkce návrháře|ActivationDependency|  
|Funkce návrháře|UpgradeAction|  
|Návrháře balíčků|SafeControl –|  
|Návrháře balíčků|CodeAccessSecurity|  
  
## <a name="feature-manifest-elements"></a>Prvky manifestu funkce
 V následující tabulce je seznam všech prvků manifestu funkce, které by se daly sloučit a jejich jedinečný klíč, který se používá k porovnání.  
  
|Název elementu|Jedinečný klíč|  
|------------------|----------------|  
|Funkce (všechny atributy)|*Atribut název* (každý atribut název elementu funkce je jedinečný klíč.)|  
|ElementFile|Umístění|  
|ElementManifests/ElementManifest|Umístění|  
|Vlastnosti nebo vlastnost|Key|  
|CustomUpgradeAction|Název|  
|CustomUpgradeActionParameter|Název|  
  
> [!NOTE]  
>  Protože je jediný způsob, jak upravit CustomUpgradeAction element ve vlastní [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] editor, účinek není slučování je nízká.  
  
## <a name="package-manifest-elements"></a>Elementy manifestu balíčku
 V následující tabulce je seznam všech elementů manifestu balíčku, které by se daly sloučit a jejich jedinečný klíč, který se používá k porovnání.  
  
|Název elementu|Jedinečný klíč|  
|------------------|----------------|  
|Řešení (všechny atributy)|*Atribut název* (každý atribut název prvku řešení je jedinečný klíč.)|  
|ApplicationResourceFiles/ApplicationResourceFile|Umístění|  
|Sestavení a sestavení|Umístění|  
|ClassResources/ClassResource|Umístění|  
|Soubor DwpFiles nebo DWP|Umístění|  
|FeatureManifests/FeatureManifest|Umístění|  
|Prostředky nebo prostředků|Umístění|  
|RootFiles/RootFile|Umístění|  
|SiteDefinitionManifests/SiteDefinitionManifest|Umístění|  
|WebTempFile|Umístění|  
|TemplateFiles/TemplateFile|Umístění|  
|SolutionDependency|SolutionID|  
  
## <a name="manually-add-deployed-files"></a>Ručně přidat nasazené soubory
 Některé manifestu prvky, jako jsou například ApplicationResourceFile a DwpFiles, zadejte umístění, které obsahuje název souboru. Však přidání položky název souboru manifestu šablony nepřidává žádné další podkladový soubor balíčku. Soubor musí přidat k projektu a její zahrnutí do balíčku nastavte vlastnost typu nasazení odpovídajícím způsobem.  
  
## <a name="see-also"></a>Viz také:
 [Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Vytváření a ladění řešení služby SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
