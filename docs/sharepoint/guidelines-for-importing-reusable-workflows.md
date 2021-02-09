---
title: Pokyny pro import opakovaně použitelných pracovních postupů | Microsoft Docs
description: Přečtěte si pokyny pro import opakovaně použitelných pracovních postupů, které byly vytvořeny v aplikaci SharePoint Designer, do sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, reusable workflows
- importing items [SharePoint development in Visual Studio]
- reusable workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a8fbf218f032c9d580c490f91f6169681dc93cef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876690"
---
# <a name="guidelines-for-importing-reusable-workflows"></a>Pokyny pro import opakovaně použitelných pracovních postupů
  K importu opakovaně použitelných pracovních postupů vytvořených v Návrháři služby SharePoint použijte šablonu projektu importovat opakovaně použitelnou pracovní postup služby SharePoint 2010 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Tato šablona importuje *deklarativní* *pracovní postup* ( [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] pouze) a převede jej na *pracovní postup kódu*, což je pracovní postup, který lze vylepšit pomocí [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] kódu nebo [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] . [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Návod: import opakovaně použitelného pracovního postupu návrháře služby SharePoint do sady Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).

 Šablona pracovního postupu import opakovaně použitelných služeb SharePoint 2010 ale může importovat jenom řešení farmy. Pokud chcete svůj pracovní postup nasadit jako řešení v izolovaném prostoru, importujte ho pomocí šablony balíčku řešení pro import SharePoint 2010. Díky tomu však nelze převést na pracovní postup kódu a nebude ho možné upravovat jako takový.

## <a name="import-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>Import opakovaně použitelných pracovních postupů pomocí šablony pro import opakovaně použitelných pracovních postupů
 Pokud naimportujete opakovaně použitelný pracovní postup pomocí šablony pracovního postupu importovat opakovaně použitelnou sadu SharePoint 2010, můžete řešení spustit nebo změnit stejně jako jakékoli jiné [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] řešení služby SharePoint, ale možná budete muset některé položky opravit ručně.

### <a name="import-task-forms"></a>Importovat formuláře úkolu
 Šablona projektu importovat opakovaně použitelnou pracovní postup služby SharePoint 2010 importuje všechny formuláře inicializace a přidružení, ale importuje pouze jeden formulář úkolu, protože schéma pracovního postupu kódu povoluje pouze jeden formulář úkolu. Všechny další formuláře úkolů z původního řešení pracovního postupu jsou umístěny do složky **ostatní importované soubory** v **Průzkumník řešení**.

## <a name="import-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>Import opakovaně použitelných pracovních postupů pomocí šablony balíčku řešení pro import sady SharePoint 2010
 Pokud importujete opakovaně použitelný pracovní postup pomocí šablony balíčku řešení pro import sady SharePoint 2010, je nutné vzít v úvahu následující problémy:

- Po importu pracovního postupu ho můžete hned nasadit a spustit v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kliknutím na klávesu **F5** . Pokud však v importovaném řešení změníte cokoli v pracovním postupu, bude pravděpodobně nutné ručně opravit prvky v projektu předtím, než bude možné tento pracovní postup nasadit a spustit.

- Vzhledem k tomu, že je pracovní postup deklarativní, nelze do něj přidat kód. Chcete-li převést pracovní postup na pracovní postup kódu, je nutné jej importovat do pomocí [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] šablony pracovního postupu importovat opakovaně použitelnou sadu SharePoint 2010.

- I když můžete v zobrazení Návrh upravit soubor návrháře pracovních postupů (. XOML), doporučuje se ho upravovat v zobrazení zdroje, protože Návrhář pracovního postupu zobrazuje falešně nepravdivé chyby.

- Ladění v pracovním postupu nefunguje pro deklarativní obsah. Zarážky nastavené v [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] nejsou k dispozice.

## <a name="import-globally-reusable-workflow-solutions"></a>Import globálně opakovaně použitelných řešení pracovního postupu
 Globálně opakovaně použitelné pracovní postupy nelze importovat pomocí šablony pracovního postupu importovat opakovaně použitelnou sadu SharePoint 2010. Pokud chcete importovat globálně opakovaně použitelný pracovní postup, musíte ho převést na neglobálně opakovaně použitelný pracovní postup nebo musíte použít šablonu balíčku řešení pro import sady SharePoint 2010.

 Chcete-li převést pracovní postup, vytvořte kopii globálně opakovaně použitelného pracovního postupu v Návrháři služby SharePoint (otevřením místní nabídky pro pracovní postup a následným výběrem možnosti **Uložit jako kopii**). Pak importujte nový opakovaně použitelný pracovní postup s šablonou pracovního postupu import opakovaně použitelných pracovních postupů služby SharePoint 2010 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 Pokud chcete importovat globálně opakovaně použitelný pracovní postup beze změny, použijte šablonu balíčku řešení pro import SharePoint 2010. Pokud použijete tuto metodu, pracovní postup není převeden na pracovní postup kódu a zůstane deklarativní pracovní postup.

## <a name="see-also"></a>Viz také
- [Import položek z existujícího webu služby SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Návod: import opakovaně použitelného pracovního postupu návrháře služby SharePoint do sady Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)
