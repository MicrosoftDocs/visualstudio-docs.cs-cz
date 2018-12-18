---
title: Pokyny pro import znovu použitelné pracovní postupy | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, reusable workflows
- importing items [SharePoint development in Visual Studio]
- reusable workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ededaae56e9d09072e236036c15a2ccd662a952e
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326462"
---
# <a name="guidelines-for-importing-reusable-workflows"></a>Pokyny pro import znovu použitelné pracovní postupy
  Provést import znovu použitelné pracovní postupy vytvořené v seznamu služby SharePoint, použijte šablonu projektu Import opakovaně použitelného SharePoint 2010 pracovního postupu v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Tato šablona importuje *deklarativní* *pracovního postupu* ([!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-pouze) a převede jej do *kód pracovního postupu*, což je pracovní postup, který můžete vylepšit pomocí [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] kódu. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Návod: Import opakovaně použitelného pracovního postupu návrháře služby SharePoint do sady Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
 Import opakovaně použitelného 2010 pracovního postupu služby SharePoint šablony však můžete importovat pouze řešení ve farmách. Pokud chcete nasadit jako řešení v izolovaném prostoru pracovní postup, můžete ho importujte pomocí šablony importem balíčku řešení služby SharePoint 2010. Tímto způsobem, ale nelze převést kód pracovního postupu a nebude možné upravit ho jako takový.  
  
## <a name="import-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>Import znovu použitelné pracovní postupy, a to pomocí šablony Import opakovaně použitelného pracovního postupu
 Pokud import opakovaně použitelného pracovního postupu pomocí šablony Import opakovaně použitelného SharePoint 2010 pracovního postupu, můžete spustit nebo změnit řešení stejně jako libovolný jiný [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] řešení služby SharePoint, ale může být nutné ručně odstranit některé položky.  
  
### <a name="import-task-forms"></a>Import formuláře úkolů
 Šablona projektu pracovního postupu Import opakovaně použitelného služby SharePoint 2010 importuje všech formulářů přidružení a zahájení, ale importuje formuláře pouze jednu úlohu, protože schéma kód pracovního postupu umožňuje pouze jedna úloha formuláře. Žádné další úlohy formuláře z původní řešení pracovního postupu jsou vloženy do **ostatní soubory importovat** složky v **Průzkumníku řešení**.  
  
## <a name="import-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>Import znovu použitelné pracovní postupy, a to pomocí šablony importu služby SharePoint 2010 řešení balíčku
 Pokud import opakovaně použitelného pracovního postupu pomocí šablony importem balíčku řešení služby SharePoint 2010, je potřeba zvážit následující problémy:  
  
-   Po importu pracovního postupu, které okamžitě můžete nasadit a spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] výběrem **F5** klíč. Pokud změníte nic v pracovním postupu v importovaných řešení, může ale muset ručně opravte elementy v projektu, než bude možné nasadit a spustit pracovní postup.  
  
-   Protože pracovní postup je deklarativní, kód nelze přidat k němu. Převést do pracovního postupu kód pracovního postupu, je nutné naimportovat do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pomocí šablony Import opakovaně použitelného 2010 pracovního postupu služby SharePoint.  
  
-   Při můžete upravit v zobrazení návrhu návrháře (XOML) soubor pracovního postupu, je doporučeno upravit v zobrazení zdroje, protože návrháře pracovních postupů zobrazí false chyby.  
  
-   Ladění v pracovním postupu nefunguje, pokud je pro deklarativní obsah. Nastavte zarážky v [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] nejsou přístupů.  
  
## <a name="import-globally-reusable-workflow-solutions"></a>Import globálně opakovaně použitelného pracovního postupu řešení
 Globálně znovu použitelné pracovní postupy nelze importovat, a to pomocí šablony Import opakovaně použitelného SharePoint 2010 pracovního postupu. Chcete-li importovat globální opakovaně použitelného pracovního postupu, je nutné ji převést na jiný globálně opakovaně použitelného pracovního postupu nebo budete muset použít šablonu importem balíčku řešení služby SharePoint 2010.  
  
 Převést pracovního postupu, vytvořit kopii globálně opakovaně použitelného pracovního postupu služby SharePoint Designer (otevřením místní nabídky pro pracovní postup a pak vyberete **uložit jako kopii**). Importovat novou opakovaně použitelného pracovního postupu pomocí šablony Import opakovaně použitelného SharePoint 2010 pracovního postupu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Pokud chcete importovat globální opakovaně použitelného pracovního postupu bez provádění úprav, použijte šablonu importem balíčku řešení služby SharePoint 2010. Pokud použijete tuto metodu, pracovní postup není převést na kód pracovního postupu a zůstane deklarativní pracovního postupu.  
  
## <a name="see-also"></a>Viz také:
 [Import položek z existující stránky SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Návod: Importujte opakovaně použitelného pracovního postupu návrháře služby SharePoint do sady Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)  
  
  
