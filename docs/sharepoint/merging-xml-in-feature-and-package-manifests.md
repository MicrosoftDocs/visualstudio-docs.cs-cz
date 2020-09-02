---
title: Slučuje se XML v manifestech funkcí a balíčků | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1378cddbc9770af923a98f1b7083a8792874b5b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64806747"
---
# <a name="merge-xml-in-feature-and-package-manifests"></a>Sloučit XML v manifestech funkcí a balíčků
  Funkce a balíčky jsou definovány [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] soubory manifestu. Tyto zabalené manifesty jsou kombinací dat generovaných návrháři a vlastními [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] zadanými v šabloně manifestu uživateli. V době vytváření balíčku [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sloučí vlastní [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] příkazy s návrhářem – je k dispozici [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] pro vytvoření balíčku [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] souboru manifestu. Podobné prvky s výjimkami zaznamenanými později v případě výjimek sloučení jsou sloučeny, aby nedocházelo k [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] chybám ověřování po nasazení souborů do služby SharePoint a aby soubory manifestu byly menší a efektivnější.

## <a name="modify-the-manifests"></a>Upravit manifesty
 Balíčky souborů manifestu nelze přímo upravovat, dokud nezakážete funkci nebo návrháře balíčku. Můžete však ručně přidat vlastní [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] prvky do šablony manifestu buď prostřednictvím návrháře funkcí a balíčků, nebo pomocí [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] editoru. Další informace naleznete v tématu [Postupy: přizpůsobení funkce služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md) a [Postupy: Přizpůsobení balíčku řešení služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

## <a name="feature-and-package-manifest-merge-process"></a>Proces sloučení manifestu funkce a balíčku
 Při kombinaci vlastních prvků spolu s prvky poskytnutými návrhářem [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] používá následující proces. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kontroluje, zda má každý prvek jedinečnou hodnotu klíče. Pokud element nemá žádnou jedinečnou hodnotu klíče, je připojen k zabalenému souboru manifestu. Podobně prvky, které mají více klíčů, nelze sloučit. Proto jsou připojeny k souboru manifestu.

 Pokud má element jedinečný klíč, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] porovná hodnoty návrháře a vlastních klíčů. Pokud se hodnoty shodují, sloučí se do jedné hodnoty. Pokud se hodnoty liší, hodnota klíč návrháře se zahodí a použije se hodnota vlastního klíče. Kolekce jsou také sloučeny. Například pokud návrhář vygeneroval [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] a vlastní [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] oba obsahují kolekci sestavení, zabalený manifest obsahuje pouze jednu kolekci sestavení.

## <a name="merge-exceptions"></a>Sloučit výjimky
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sloučí většinu prvků návrháře [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] spolu s podobnými vlastními [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] prvky, pokud mají jediný jedinečný identifikující atribut. Některé prvky ale nemají jedinečný identifikátor vyžadovaný pro [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] sloučení. Tyto prvky jsou známé jako *výjimky sloučení*. V těchto případech [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nesloučí vlastní [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] prvky spolu s prvky poskytnutými návrhářem [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] , ale místo toho je připojí do zabaleného souboru manifestu.

 Následuje seznam výjimek sloučení pro funkce a [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] soubory manifestu balíčku.

|Návrhář|XML – element|
|--------------|-----------------|
|Návrhář funkcí|ActivationDependency|
|Návrhář funkcí|UpgradeAction|
|Návrhář balíčku|SafeControl –|
|Návrhář balíčku|CodeAccessSecurity|

## <a name="feature-manifest-elements"></a>Prvky manifestu funkce
 Následující tabulka je seznam všech prvků manifestu funkce, které lze sloučit, a jejich jedinečný klíč, který se používá pro porovnání.

|Název prvku|Jedinečný klíč|
|------------------|----------------|
|Funkce (všechny atributy)|*Název atributu* (každý název atributu prvku funkce je jedinečný klíč)|
|ElementFile|Umístění|
|ElementManifests/ElementManifest|Umístění|
|Vlastnosti/vlastnost|Klíč|
|CustomUpgradeAction|Název|
|CustomUpgradeActionParameter|Název|

> [!NOTE]
> Vzhledem k tomu, že jediný způsob, jak upravit element CustomUpgradeAction je ve vlastním [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] editoru, není k dispozici žádný efekt sloučení.

## <a name="package-manifest-elements"></a>Prvky manifestu balíčku
 Následující tabulka uvádí seznam všech prvků manifestu balíčku, které lze sloučit, a jejich jedinečný klíč, který se používá pro porovnání.

|Název prvku|Jedinečný klíč|
|------------------|----------------|
|Řešení (všechny atributy)|*Název atributu* (každý název atributu prvku řešení je jedinečný klíč)|
|ApplicationResourceFiles/ApplicationResourceFile|Umístění|
|Sestavení/sestavení|Umístění|
|ClassResources/ClassResource|Umístění|
|DwpFiles/DwpFile|Umístění|
|FeatureManifests/FeatureManifest|Umístění|
|Prostředky/prostředky|Umístění|
|RootFiles/RootFile|Umístění|
|SiteDefinitionManifests/SiteDefinitionManifest|Umístění|
|WebTempFile|Umístění|
|TemplateFiles/TemplateFile|Umístění|
|SolutionDependency|SolutionID|

## <a name="manually-add-deployed-files"></a>Ruční přidání nasazených souborů
 Některé prvky manifestu, například ApplicationResourceFile a DwpFiles, určují umístění, které obsahuje název souboru. Přidání položky názvu souboru do šablony manifestu však nepřidá do balíčku základní soubor. Tento soubor je nutné přidat do projektu, aby jej bylo možné zahrnout do balíčku a odpovídajícím způsobem nastavit vlastnost typu nasazení.

## <a name="see-also"></a>Viz také
- [Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Sestavování a ladění řešení služby SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
