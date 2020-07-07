---
title: 'Návrhář balíčku: Přidání & odebrání funkcí a položek do balíčku'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerDesign
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4dfbda711c42e475af5f17c8799e53b13e26611a
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014604"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer"></a>Postupy: Přidání a odebrání funkcí a položek do balíčku pomocí návrháře balíčků
  Když vytvoříte řešení služby SharePoint, sada Visual Studio přidá do balíčku v řešení výchozí funkce služby SharePoint. Před konečným nasazením můžete přidat a odebrat položky a funkce projektu služby SharePoint pro úpravu balíčku služby SharePoint.

 Alternativně můžete použít Průzkumníka balíčků k přidání a odebrání položek projektu služby SharePoint. Můžete také zobrazit a změnit hierarchii položek projektu služby SharePoint a funkcí, které jsou vloženy do balíčku (. wsp). Další informace najdete v tématu [Postup: Přidání a odebrání funkcí a položek do balíčku pomocí Průzkumníka balíčků](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

## <a name="add-features-to-a-sharepoint-package"></a>Přidání funkcí do balíčku služby SharePoint
 K přidání funkcí do balíčku služby SharePoint můžete použít Návrhář balíčků.

#### <a name="to-add-sharepoint-features-with-the-package-designer"></a>Přidání funkcí služby SharePoint pomocí návrháře balíčků

1. Otevřete **Návrháře balíčků**.

    Další informace najdete v tématu [Postup: Přizpůsobení balíčku řešení služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Pomocí jednoho nebo několika následujících kroků přidejte jednu nebo více funkcí služby SharePoint:

   1. Dvakrát klikněte na jednotlivé položky v seznamu **řešení** , které chcete přidat.

   2. Zvolte položku, kterou chcete přidat, a poté klikněte na tlačítko **Přidat** (>).

   3. Klikněte na tlačítko **Přidat vše** (>>), chcete-li přidat všechny položky najednou.

      Můžete například dvakrát kliknout na položku v seznamu **řešení** a přidat ji k **položkám v seznamu balíčků** .

      Položky projektu služby SharePoint a funkce se zobrazí v **položkách v seznamu balíčků** .

## <a name="remove-features-from-a-sharepoint-package"></a>Odebrání funkcí ze SharePointového balíčku
 K odebrání funkcí do balíčku služby SharePoint můžete použít Návrhář balíčků.

#### <a name="to-remove-sharepoint-features-with-the-package-designer"></a>Odebrání funkcí služby SharePoint pomocí návrháře balíčků

1. V **položkách v seznamu balíček** zvolte položku, kterou chcete odebrat, a pak zvolte tlačítko **Odebrat** (<), nebo zvolte tlačítko **Odebrat vše** (<<) a odeberte všechny položky.

     Položky SharePointu se zobrazí v **položkách v seznamu řešení** .

## <a name="see-also"></a>Viz také:
- [Vytváření balíčků řešení služby SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Postupy: Přizpůsobení balíčku řešení služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Postupy: vytvoření balíčku](https://msdn.microsoft.com/b24be45c-e91d-49bb-afb0-7b265404214b)
