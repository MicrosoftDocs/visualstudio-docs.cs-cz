---
title: Vytváření funkcí služby SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 56bc4dbd50bedc15fcf6c69cbc334fe09c6094cc
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36325596"
---
# <a name="create-sharepoint-features"></a>Vytváření funkcí služby SharePoint
  Funkce služby SharePoint můžete použít k seskupení souvisejících položek projektu služby SharePoint pro snazší nasazení. Můžete vytvořit funkce, nastavení rozsahů a označit další funkce, jako závislosti pomocí návrháře funkce služby SharePoint. Návrhář vytvoří také manifestu, který je soubor XML, který popisuje každou funkci.  
  
## <a name="add-features-to-the-sharepoint-solution"></a>Přidání funkce do řešení služby SharePoint
 Pomocí Průzkumníka řešení nebo Průzkumníku balíčků můžete přidání funkce do řešení služby SharePoint. Jeden z následujících metod slouží k přidání funkce.  
  
-   V **Průzkumníku řešení**, otevřete místní nabídku pro **funkce**a potom zvolte **přidat funkce**.  
  
-   V **Průzkumníku balíčků**, otevřete místní nabídku pro balíček a potom zvolte **přidat funkce**.  
  
## <a name="using-the-feature-designer"></a>Pomocí funkce návrháře
 Řešení služby SharePoint může obsahovat jednu nebo několik funkcí služby SharePoint, které jsou seskupené v rámci uzlu funkce v Průzkumníku řešení. Jednotlivé funkce má svou vlastní **funkce Návrhář** , můžete upravit vlastnosti funkcí. Další informace najdete v tématu [postupy: přizpůsobení funkce služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md). K rozlišení funkce jeden z druhého, můžete konfigurovat vlastnosti funkce jako je například název, popis, verze a obor.  
  
### <a name="feature-designer-options"></a>Možnosti funkcí, které návrháře
 Po vytvoření funkce, můžete přizpůsobit funkce návrháře.  
  
 Následující tabulka popisuje vlastnosti funkcí, které se zobrazují v Návrháři funkce.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|Název|Volitelné. Výchozí název funkce je nastaven na *název řešení SolutionName* *FeatureName*.|  
|Popis|Volitelné. Popis funkce služby SharePoint.|  
|Rozsah|Požadováno. Pokud funkce je vytvořená pomocí **Průzkumníku řešení**, na Web ve výchozím nastavení oboru.<br /><br /> -Farmy: Aktivace funkce pro farmu služby celý server.<br /><br /> -Site: Aktivujte funkci pro všechny weby v kolekci webů.<br /><br /> -Webové: Aktivace funkce pro konkrétní web.<br /><br /> -WebApplication: Aktivujte funkci pro všechny webové servery ve webové aplikaci.|  
|Položky v řešení|Všechny položky služby SharePoint, které mohou být přidány do funkce.|  
|Položky ve funkci|Položky projektu služby SharePoint, které jsou přidané do funkce.|  
  
## <a name="add-and-remove-sharepoint-project-items"></a>Přidání a odebrání položek projektu služby SharePoint
 Můžete vybrat položky projektu služby SharePoint, které chcete přidat funkce služby SharePoint k nasazení. Použití **funkce Návrhář** k přidání a odebrání položek z funkcí a funkce v manifestu. Další informace najdete v tématu [postupy: Přidání a odebrání položek z funkcí služby SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md).  
  
## <a name="add-feature-dependencies"></a>Přidání funkcí
 Manifest funkce můžete nakonfigurovat tak, aby SharePoint server aktivuje některých funkcí, než je zapnuta. Například pokud vaše funkce služby SharePoint závisí na dalších funkcí pro funkce nebo data, serveru SharePoint mohou zkuste je napřed k aktivaci žádné funkce, které vaše funkce závisí na. Další informace najdete v tématu [postupy: Přidání a odebrání závislostí funkce](../sharepoint/how-to-add-and-remove-feature-dependencies.md).  
  
## <a name="see-also"></a>Viz také:
 [Postupy: přizpůsobení funkce služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Postupy: Přidání a odebrání položek z funkcí služby SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
 [Postupy: Přidání a odebrání závislostí funkce](../sharepoint/how-to-add-and-remove-feature-dependencies.md)  
  
  
