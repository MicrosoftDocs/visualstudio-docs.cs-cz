---
title: Vytváření funkcí služby SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8d3f453770dbb389a688db0a9edcc8e97e179858
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952737"
---
# <a name="create-sharepoint-features"></a>Vytvoření funkcí služby SharePoint
  Funkci služby SharePoint můžete použít k seskupení souvisejících položek projektu služby SharePoint pro snazší nasazení. Pomocí návrháře funkcí služby SharePoint můžete vytvořit funkce, nastavit obory a označit jiné funkce jako závislosti. Návrhář také generuje manifest, což je soubor XML, který popisuje jednotlivé funkce.

## <a name="add-features-to-the-sharepoint-solution"></a>Přidání funkcí do řešení služby SharePoint
 Funkci můžete přidat do řešení služby SharePoint pomocí Průzkumník řešení nebo Průzkumníka balíčků. K přidání funkce můžete použít jednu z následujících metod.

- V **Průzkumník řešení**otevřete místní nabídku pro **funkce**a zvolte možnost **Přidat funkci**.

- V **Průzkumníku balení**otevřete místní nabídku balíčku a zvolte možnost **Přidat funkci**.

## <a name="using-the-feature-designer"></a>Pomocí návrháře funkcí
 Řešení služby SharePoint může obsahovat jednu nebo více funkcí služby SharePoint, které jsou seskupeny pod uzlem funkce v Průzkumník řešení. Každá funkce má svůj vlastní **Návrhář funkcí** , který můžete použít k přizpůsobení vlastností funkce. Další informace naleznete v tématu [How to: Customize a SharePoint Feature](../sharepoint/how-to-customize-a-sharepoint-feature.md). Pro odlišení dalších funkcí můžete nakonfigurovat vlastnosti funkce, jako je název, popis, verze a obor.

### <a name="feature-designer-options"></a>Možnosti návrháře funkcí
 Když vytvoříte funkci, můžete ji přizpůsobit pomocí návrháře funkcí.

 Následující tabulka popisuje vlastnosti funkce, které se zobrazují v Návrháři funkcí.

|Vlastnost|Popis|
|--------------|-----------------|
|Nadpis|Nepovinný parametr. Výchozí *název funkce je nastaven na* *vlastnost*název souboru.|
|Popis|Nepovinný parametr. Popis funkce SharePointu|
|Obor|Povinná hodnota. Pokud se funkce vytvoří pomocí **Průzkumník řešení**, obor je ve výchozím nastavení nastavený na web.<br /><br /> -Farma: Aktivujte funkci pro celou serverovou farmu.<br /><br /> -Site: aktivuje funkci pro všechny weby v kolekci webů.<br /><br /> -Web: aktivuje funkci pro určitý web.<br /><br /> -WebApplication: aktivuje funkci pro všechny weby ve webové aplikaci.|
|Položky v řešení|Všechny položky SharePointu, které lze přidat do funkce.|
|Položky v této funkci|Položky projektu služby SharePoint, které byly přidány do funkce.|

## <a name="add-and-remove-sharepoint-project-items"></a>Přidání a odebrání položek projektu služby SharePoint
 Můžete vybrat, které položky projektu služby SharePoint chcete přidat funkci služby SharePoint pro nasazení. Pomocí **návrháře funkcí** můžete přidat a odebrat položky funkcí a zobrazit manifest funkce. Další informace najdete v tématu [Postup: Přidání a odebrání položek funkcí služby SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md).

## <a name="add-feature-dependencies"></a>Přidat závislosti funkcí
 Manifest funkce můžete nakonfigurovat tak, aby server SharePoint před aktivací vaší funkce aktivoval určité funkce. Například pokud vaše funkce služby SharePoint závisí na dalších funkcích pro funkce nebo data, může se server služby SharePoint nejprve pokusit aktivovat některou z funkcí, na kterých závisí vaše funkce. Další informace najdete v tématu [Postup: Přidání a odebrání závislostí funkcí](../sharepoint/how-to-add-and-remove-feature-dependencies.md).

## <a name="see-also"></a>Viz také
- [Postupy: přizpůsobení funkce služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Postupy: přidávání a odebírání položek do funkcí služby SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
- [Postupy: Přidání a odebrání závislostí funkcí](../sharepoint/how-to-add-and-remove-feature-dependencies.md)
