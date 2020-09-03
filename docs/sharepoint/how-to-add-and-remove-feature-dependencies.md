---
title: 'Postupy: Přidání a odebrání závislostí funkcí | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW
- VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c318a7dc4672a10e993d0149ec77e7f94679d465
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86014780"
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>Postupy: Přidání a odebrání závislostí funkcí
  Funkce SharePointu může záviset na dalších funkcích pro funkce nebo data. V těchto případech můžete tyto další funkce označit jako závislosti pro vaši funkci. Tímto způsobem server SharePoint zajišťuje, aby byly před aktivací vaší funkce aktivovány závislé funkce.

## <a name="add-dependencies"></a>Přidat závislosti
 Do řešení můžete přidat další funkce jako závislosti. Tímto způsobem se můžete ujistit, že jsou nainstalované a aktivované požadované funkce před instalací vaší funkce.

#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>Přidání závislosti na funkci v řešení

1. Otevřete návrháře funkcí, rozbalte uzel **závislosti aktivace funkcí** a pak klikněte na tlačítko **Přidat** .

2. V dialogovém okně **přidat závislosti aktivace funkce** zvolte možnost **Přidat závislost na funkce** na tlačítku řešení, vyberte název funkce, kterou chcete přidat jako závislost, a poté klikněte na tlačítko **Přidat** .

     Více než jednu funkci můžete přidat tak, že při výběru klávesy **CTRL** vyberete více názvů.

## <a name="addi-custom-dependencies"></a>Addi vlastní závislosti
 Můžete přidat funkce, které jsou již nasazeny na serveru SharePoint jako závislost. Tímto způsobem ověří proces aktivace služby SharePoint, aby se zajistilo, že všechny závislé funkce budou aktivovány před instalací vaší funkce.

#### <a name="to-add-a-dependency-by-the-feature-id"></a>Přidání závislosti podle ID funkce

1. Otevřete návrháře funkcí, rozbalte uzel **závislosti aktivace funkcí** a pak klikněte na tlačítko **Přidat** .

2. V dialogovém okně **přidat závislosti aktivace funkce** klikněte na tlačítko možnosti **Přidat vlastní závislost** .

3. Do textového pole **ID funkce** zadejte identifikátor GUID funkce, kterou chcete označit jako závislost aktivace, a pak klikněte na tlačítko **Přidat** .

## <a name="edit-custom-dependencies"></a>Upravit vlastní závislosti
 Můžete upravit vlastní závislosti, které jste přidali dříve. Závislé funkce, které jsou ve vašem řešení, je ale možné odebrat, nikoli upravovat.

#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>Změna závislosti funkce v řešení

1. Otevřete Návrhář funkcí a potom rozbalte uzel **závislosti aktivace funkcí** .

2. Zvolte název funkce, kterou chcete upravit, a pak klikněte na tlačítko **Upravit** .

3. V dialogovém okně **Upravit závislost aktivace vlastních funkcí** změňte název, ID funkce nebo popis a pak klikněte na tlačítko **Odeslat** .

## <a name="remove-dependencies"></a>Odebrat závislosti

#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>Postup odebrání závislosti na funkci v řešení

1. V Návrháři funkcí rozbalte uzel **závislosti aktivace funkcí** , vyberte název funkce, kterou chcete odebrat, a poté klikněte na tlačítko **Odebrat** .

## <a name="see-also"></a>Viz také
- [Vytvoření funkcí služby SharePoint](../sharepoint/creating-sharepoint-features.md)
- [Postupy: přizpůsobení funkce služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Postupy: přidávání a odebírání položek do funkcí služby SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
