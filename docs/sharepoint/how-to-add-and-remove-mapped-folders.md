---
title: 'Postupy: Přidání a odebrání mapovaných složek | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.Project.MappedFolder
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, mapped folders
- mapped folders [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 80fbd3e18b8d440eae2873c73013ad7468073640
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014651"
---
# <a name="how-to-add-and-remove-mapped-folders"></a>Postupy: Přidání a odebrání mapovaných složek
  Některé běžně používané složky v SharePointu, jako jsou obrázky a rozložení, jsou hluboko vložené v hierarchii souborů. Tyto složky lze namapovat na projekt služby SharePoint pro snazší přístup k nim. Mapované složky jsou složky v projektu služby SharePoint, které odpovídají fyzickému umístění souborů v instalaci serveru SharePoint.

 Když nasadíte aplikaci služby SharePoint, obsah mapované složky a všech jejích podsložek bude zkopírován balíčkem řešení (. wsp) na server, na kterém je spuštěna služba SharePoint, v zadaném umístění ve stromu složek služby SharePoint. Toto umístění je určeno vlastností **umístění nasazení** , která je nastavena pro mapovanou složku. Všechny podsložky v mapované složce jsou relativní vzhledem k **umístění nasazení** mapované složky. Všimněte si, že vlastnost **umístění nasazení** , nikoli název mapované složky, určuje, kde jsou položky nasazeny.
Mapované složky můžete přidat do projektu pomocí příkazů na panelu nabídek nebo v místní nabídce projektu. Chcete-li přidat tyto mapované složky, které se používají nejčastěji, můžete použít **namapovanou složku "image SharePoint** " a **Přidat do ní příkazy složky SharePoint "rozložení"** . Můžete namapovat libovolné další dostupné složky SharePointu na projekt pomocí příkazu **přidat SharePoint mapované složky** v místní nabídce a následně zadat složky v dialogovém okně **přidat SharePoint mapované složky** .

## <a name="add-mapped-folders-to-a-project"></a>Přidání mapovaných složek do projektu
 Následující postup popisuje, jak přidat dvě mapované složky do projektu vizuální webové části. Chcete-li začít, vytvořte projekt Visual Web Part.

#### <a name="to-add-mapped-folders-to-a-project"></a>Přidání mapovaných složek do projektu

1. Na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

2. V dialogovém okně **Nový projekt** rozbalte uzel **Visual Basic** nebo **Visual C#** , rozbalte uzel **Office/SharePoint** a pak zvolte uzel **řešení služby SharePoint** .

3. V seznamu šablon projektů vyberte šablonu **Visual Web Part sady SharePoint 2013** .

4. Do pole **název** zadejte **TestProject1**a poté klikněte na tlačítko **OK** .

5. V **Průvodci vlastním nastavením služby SharePoint**klikněte na tlačítko **Dokončit** a zachovejte výchozí nastavení.

6. V **Průzkumník řešení**zvolte uzel projektu a potom v řádku nabídek zvolte **projekt**  >  **Přidat namapovanou složku SharePoint "obrázky"**.

     Složka s názvem **Image** se zobrazí ve vašem projektu a obsahuje podsložku s názvem TestProject1. Tato mapovaná složka bude obsahovat obrázky pro projekt Visual Web Part.

7. V **Průzkumník řešení**zvolte uzel projektu a pak na panelu nabídek zvolte **projekt**  >  **přidat SharePoint mapované složky** . zobrazí se dialogové okno **přidat SharePoint mapované složky** .

8. Ve stromovém zobrazení složek, které jsou k dispozici pro mapování, zvolte složku **prostředky** a pak klikněte na tlačítko **OK** .

     Ve vašem projektu se zobrazí složka s názvem **prostředky** . Tato složka může ukládat položky jako řetězcové soubory prostředků. Podsložky mohou být užitečné pro uspořádání obsahu mapované složky, nejsou však vytvořeny automaticky při přidání mapované složky pomocí příkazu **přidat SharePoint mapované složky** . Chcete-li přidat podsložku, zvolte složku **prostředky** a poté v panelu nabídky zvolte možnost **projekt**  >  **Nová složka**.

## <a name="change-the-deployment-location-of-a-mapped-folder"></a>Změna umístění nasazení mapované složky
 Ve výchozím nastavení se mapované složky přidávají do konkrétních umístění relativně ke kořenové cestě instalace služby SharePoint, kterou token \<SharePointRoot> označuje. Toto umístění však můžete změnit změnou vlastnosti **umístění nasazení** mapované složky. Každá namapovaná složka má svou vlastní vlastnost **umístění nasazení** .

#### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>Změna umístění nasazení mapované složky

1. V projektu, který jste vytvořili dříve, vyberte mapovanou složku.

2. V okně **vlastnosti** klikněte na tlačítko se třemi tečkami (![Elipsa ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "Elipsa ASP.NET Mobile Designer")) ve vlastnosti **umístění nasazení** .

3. V dialogovém okně **přidat mapované složky SharePoint** přejděte do složky, do které chcete, aby namapovaná složka odkazovala.

4. Zvolte uzel a pak klikněte na tlačítko **OK** .

## <a name="rename-or-remove-mapped-folders"></a>Přejmenovat nebo odebrat mapované složky

#### <a name="to-rename-or-remove-a-mapped-folder"></a>Přejmenování nebo odebrání mapované složky

1. V projektu, který jste vytvořili dříve, vyberte mapovanou složku.

2. Chcete-li přejmenovat mapovanou složku, otevřete její místní nabídku, zvolte možnost **Přejmenovat**, zadejte nový název a stiskněte klávesu ENTER.

     Alternativně můžete zvolit mapovanou složku, kterou chcete přejmenovat, otevřít okno **vlastnosti** a nastavit hodnotu vlastnosti **název složky** na nový název.

3. Chcete-li odebrat namapovanou složku z projektu, otevřete její místní nabídku, zvolte možnost **Odstranit**a poté kliknutím na tlačítko **OK** v dialogovém okně potvrďte odebrání.

## <a name="see-also"></a>Viz také:
- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)
