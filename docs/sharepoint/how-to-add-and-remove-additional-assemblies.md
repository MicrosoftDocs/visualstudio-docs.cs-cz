---
title: 'Postupy: Přidání a odebrání dalších sestavení | Microsoft Docs'
description: Naučte se přidávat a odebírat další sestavení v balíčcích řešení služby SharePoint. Také přidejte nebo odstraňte bezpečné ovládací prvky a prostředky třídy.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.CustomAssembly
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
ms.openlocfilehash: 41b41ccd5eda2a44457adf23302a833574dade9e
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914969"
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>Postupy: Přidání a odebrání dalších sestavení
  Pokud balíček služby SharePoint závisí na jiných sestaveních pro funkce nebo data, můžete přidat sestavení do balíčku řešení (. wsp). Tímto způsobem server SharePoint zajistí, že vlastní sestavení jsou nainstalována s balíčkem.

 Můžete také přidat a změnit bezpečné ovládací prvky a soubory prostředků třídy přidružené k sestavením.

## <a name="add-additional-assemblies-safe-controls-and-class-resources"></a>Přidat další sestavení, bezpečné ovládací prvky a prostředky třídy
 Do balíčku řešení služby SharePoint můžete přidat další sestavení. Další sestavení v řešení v izolovaném prostoru se nasazují do globální mezipaměti sestavení (GAC), ale položky projektu služby SharePoint v řešení v izolovaném prostoru jsou přidány do databáze obsahu. Do těchto dalších sestavení můžete také přidat bezpečné ovládací prvky a prostředky třídy. Další informace o bezpečných ovládacích prvcích naleznete v tématu [poskytnutí informací o balení a nasazení v položkách projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) nebo "vytvoření položky SafeControl –" při [nasazení webové části ve službě SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14)).

#### <a name="to-add-an-existing-assembly"></a>Přidání existujícího sestavení

1. Otevřete **Návrháře balíčků**. Další informace najdete v tématu [Postup: Přizpůsobení balíčku řešení služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Vyberte kartu **Upřesnit** .

3. Klikněte na tlačítko **Přidat** a zvolte možnost **Přidat existující sestavení** ze seznamu.

     Zobrazí se dialogové okno **Přidat existující sestavení** .

4. Zvolte tři tečky (![ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "Elipsa ASP.NET Mobile Designer")) a pak vyberte sestavení, které chcete přidat. Pro účely přenositelnosti doporučujeme použít relativní cestu k vybranému sestavení.

5. Pro **cíl nasazení** vyberte možnost **GlobalAssemblyCache** pro nasazení sestavení do globální mezipaměti sestavení (GAC), nebo klikněte na tlačítko možnosti **WebApplication** pro nasazení sestavení do složky WebApplication na serveru, na kterém je spuštěna služba SharePoint.

#### <a name="to-add-an-assembly-from-project-output"></a>Přidání sestavení z výstupu projektu

1. Otevřete **Návrháře balíčků**.

     Další informace najdete v tématu [Postup: Přizpůsobení balíčku řešení služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Vyberte kartu **Upřesnit** .

3. Klikněte na tlačítko **Přidat** a poté ze seznamu zvolte možnost **Přidat sestavení z výstupu projektu** .

     Zobrazí se dialogové okno **Přidat sestavení z výstupu projektu** .

4. V seznamu **zdrojový projekt** a vyberte zdrojový projekt, který chcete přidat.

5. Pro **cíl nasazení** vyberte možnost **GlobalAssemblyCache** pro nasazení sestavení do globální mezipaměti sestavení (GAC), nebo klikněte na tlačítko možnosti **WebApplication** pro nasazení sestavení do složky WebApplication na serveru, na kterém je spuštěna služba SharePoint.

#### <a name="to-add-a-safe-control"></a>Postup přidání bezpečného ovládacího prvku

1. Otevřete dialogové okno **Upravit existující sestavení** . Chcete-li to provést, otevřete návrháře balíčků, zvolte kartu **Upřesnit** , zvolte sestavení a klikněte na tlačítko **Upravit** .

2. V podokně **bezpečné ovládací prvky** vyberte **kliknutím sem tlačítko Přidat novou položku** .

3. Do sloupce **název sestavení** zadejte název sestavení.

4. Do sloupce **obor názvů** zadejte název oboru názvů pro bezpečný ovládací prvek.

5. Do sloupce **název typu** zadejte název typu.

#### <a name="to-add-a-class-resource"></a>Přidání prostředku třídy

1. Otevřete dialogové okno **Upravit existující sestavení** . Chcete-li to provést, otevřete návrháře balíčků, zvolte kartu **Upřesnit** , zvolte sestavení a klikněte na tlačítko **Upravit** .

2. V podokně **prostředky třídy** klikněte na tlačítko **kliknutím sem přidejte novou položku** .

3. Ve sloupci **název souboru** klikněte na tlačítko se třemi tečkami (![Elipsa ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "Elipsa ASP.NET Mobile Designer")) a vyberte prostředek třídy, který chcete přidat.

## <a name="delete-custom-assemblies"></a>Odstranění vlastních sestavení
 Můžete odstranit sestavení z balíčku služby SharePoint nebo odstranit bezpečné ovládací prvky a prostředky třídy z existujících sestavení.

#### <a name="to-delete-an-existing-assembly"></a>Odstranění existujícího sestavení

1. Otevřete **Návrháře balíčků**. Další informace najdete v tématu [Postup: Přizpůsobení balíčku řešení služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Vyberte kartu **Upřesnit** .

3. V podokně **Další sestavení** vyberte vlastní sestavení, které chcete odstranit.

4. Klikněte na tlačítko **Odstranit** .

#### <a name="to-delete-a-safe-control-for-an-assembly"></a>Odstranění bezpečného ovládacího prvku pro sestavení

1. Otevřete dialogové okno **Upravit existující sestavení** . Chcete-li to provést, otevřete návrháře balíčků, zvolte kartu **Upřesnit** , zvolte sestavení a klikněte na tlačítko **Upravit** .

2. Vyberte bezpečný ovládací prvek, který chcete odstranit.

3. Vyberte klávesu DELETE.

#### <a name="to-delete-a-class-resource-for-an-assembly"></a>Odstranění prostředku třídy pro sestavení

1. Otevřete dialogové okno **Upravit existující sestavení** . Chcete-li to provést, otevřete návrháře balíčků, zvolte kartu **Upřesnit** , zvolte sestavení a klikněte na tlačítko **Upravit** .

2. Vyberte prostředek třídy, který chcete odstranit.

3. Vyberte klávesu DELETE.

## <a name="see-also"></a>Viz také
- [Vytvoření funkcí služby SharePoint](../sharepoint/creating-sharepoint-features.md)
- [Postupy: Přizpůsobení funkce služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Postupy: přidávání a odebírání položek do funkcí služby SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
