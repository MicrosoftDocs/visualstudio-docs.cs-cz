---
title: Vytvoření funkcí a ověření balíčku pro řešení služby SharePoint
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7ac718d16383448ea13f01ad367d97f917bb42ed
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585820"
---
# <a name="create-feature-and-package-validations-for-sharepoint-solutions"></a>Vytvoření funkcí a ověření balíčku pro řešení služby SharePoint

  Můžete vytvořit vlastní ověřovací pravidla pro ověření balíčku řešení vygenerovaného aplikací Visual Studio. Úplné ověřování pro celou funkci nebo balíček můžete provést tak, že v místní nabídce balíčku nebo funkce v **PackagingExplorer**vyberete **ověřit** . Částečné ověřování se provádí při přidávání nových položek SharePointového projektu nebo funkcí do projektu, aby bylo možné zjistit, zda by byl balíček nebo funkce v platném stavu.

### <a name="to-create-a-custom-package-validation-rule"></a>Vytvoření vlastního ověřovacího pravidla balíčku

1. Vytvořte projekt knihovny tříd.

2. Přidejte odkazy na následující sestavení:

    - Microsoft. VisualStudio. SharePoint

    - System. ComponentModel. složení

3. Vytvořte třídu, která implementuje jedno z následujících rozhraní:

    - Chcete-li vytvořit pravidlo ověření balíčku, implementujte <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> rozhraní.

    - Chcete-li vytvořit ověřovací pravidlo funkce, implementujte <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> rozhraní.

4. Přidejte <xref:System.ComponentModel.Composition.ExportAttribute> do třídy. Tento atribut umožňuje aplikaci Visual Studio zjistit a načíst ověřovací pravidlo. Předejte <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> typ nebo do konstruktoru atributu.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje, jak vytvořit vlastní ověřovací pravidlo funkce.

 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad vyžaduje odkazy na následující sestavení:

- Microsoft. VisualStudio. SharePoint.

- System. ComponentModel. složení.

## <a name="deploy-the-extension"></a>Nasazení rozšíření
 Chcete-li nasadit rozšíření, vytvořte [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] balíček rozšíření (VSIX) pro sestavení a všechny další soubory, které chcete distribuovat s rozšířením. Další informace naleznete v tématu [nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Viz také
- [Rozšiřování balení a nasazení služby SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
