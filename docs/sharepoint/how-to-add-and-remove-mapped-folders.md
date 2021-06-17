---
title: 'Postupy: Přidání a odebrání mapovaných složek | Microsoft Docs'
description: Přidání a odebrání mapovaných složek do projektu v SharePointu  Změňte umístění nasazení mapované složky. Přejmenujte nebo odeberte mapované složky.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a9b74ba786c9d1104fd507442d959e75afb17bf2
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112427"
---
# <a name="how-to-add-and-remove-mapped-folders"></a>Postupy: Přidání a odebrání mapovaných složek

  Některé běžně používané složky v SharePointu, jako jsou obrázky a rozložení, jsou hluboko vložené do hierarchie souborů. Tyto složky můžete namapovat na sharepointový projekt, abyste k nim měli přístup snadněji. Mapované složky jsou složky v projektu SharePointu, které odpovídají fyzickému umístění souborů v instalaci SharePoint Serveru.

 Když nasadíte sharepointovou aplikaci, obsah mapované složky a všech jejích podsložek se zkopíruje pomocí balíčku řešení (.wsp) na server se spuštěnou službou SharePoint v zadaném umístění ve stromu složek SharePointu. Toto umístění je určeno **vlastností Umístění nasazení** nastavenou pro namapovanou složku. Všechny podsložky v mapované složce jsou relativní vzhledem **k umístění nasazení** mapované složky. Všimněte **si, že** vlastnost Umístění nasazení, nikoli název mapované složky, určuje, kde jsou položky nasazeny.
Mapované složky můžete do projektu přidat pomocí příkazů na řádku nabídek nebo místní nabídky projektu. K přidání mapovaných složek, které se používají nejčastěji, můžete použít příkazy Přidat mapovanou složku obrázků **SharePointu** a Přidat **sharepointovou** složku Rozložení. Libovolnou z dalších dostupných sharepointových složek můžete namapovat na váš projekt pomocí příkazu Přidat mapovanou složku **SharePointu** v místní nabídce a zadáním složek v dialogovém okně Přidat mapovanou složku **SharePointu.**

## <a name="add-mapped-folders-to-a-project"></a>Přidání mapovaných složek do projektu

 Následující postup popisuje, jak přidat dvě mapované složky do projektu webové části vizuálu. Začněte tím, že vytvoříte projekt webové části vizuálu.

## <a name="to-add-mapped-folders-to-a-project"></a>Přidání mapovaných složek do projektu

1. Na řádku nabídek zvolte File New Project **(Soubor**  >  **nový**  >  **projekt).**
::: moniker range="=vs-2017"
2. V dialogovém **okně Nový** projekt rozbalte uzel **Visual Basic** nebo **Visual C#,** rozbalte uzel **Office/SharePoint** a pak zvolte uzel **Řešení služby SharePoint.**

3. V seznamu šablon projektů zvolte šablonu webové části vizuálu **SharePointu 2013.**

4. Do pole **Název** zadejte **TestProject1** a pak zvolte **tlačítko OK.**
::: moniker-end
::: moniker range=">=vs-2019"
2. V dialogovém **okně Vytvořit nový projekt** vyberte *sharepointovou* vizuální webovou část * pro konkrétní verzi SharePointu, kterou jste nainstalovali. Pokud máte například instalaci SharePointu 2019, vyberte šablonu webové části vizuálu **SharePointu 2019.**
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. Do pole **Název** zadejte **TestProject1.**
4. Pak zvolte **tlačítko** Vytvořit.
::: moniker-end

5. V **Průvodci přizpůsobením SharePointu** zvolte **tlačítko Dokončit,** aby se zachovala výchozí nastavení.

6. V **Průzkumník řešení** vyberte uzel projektu a pak v řádku nabídek zvolte **Project**  >  **Add SharePoint "Images" Mapped Folder (Projekt – přidat sharepointovou "obrázky" mapovanou složku).**

     V projektu se zobrazí složka s názvem **Images,** která obsahuje podsložku s názvem TestProject1. Tato mapovaná složka bude obsahovat obrázky pro projekt webové části vizuálu.

7. V **Průzkumník řešení** vyberte uzel projektu a pak v řádku nabídek zvolte **Project** Add SharePoint Mapped Folder (Projekt – přidat mapovanou složku SharePointu). Zobrazí se dialogové okno Přidat mapovanou složku  >   **SharePointu.**

8. Ve stromovém zobrazení složek, které jsou k dispozici pro mapování, zvolte **složku Prostředky** a pak zvolte **tlačítko OK.**

     V projektu se zobrazí **složka s** názvem Resources (Prostředky). Tato složka může ukládat položky, jako jsou soubory prostředků řetězců. Podsložky mohou být užitečné pro uspořádání obsahu mapované složky, ale při přidání mapované složky pomocí příkazu Přidat mapovanou složku **SharePointu** se automaticky nevystaví. Pokud chcete přidat podsadu, zvolte složku **Resources** (Prostředky) a pak v řádku nabídek zvolte Project New Folder   >  **(Projektová nová složka).**

## <a name="change-the-deployment-location-of-a-mapped-folder"></a>Změna umístění nasazení mapované složky

 Ve výchozím nastavení se mapované složky přidávají do konkrétních umístění vzhledem ke kořenové instalační cestě SharePointu, kterou token \<SharePointRoot> označuje. Toto umístění však můžete změnit změnou vlastnosti **Umístění nasazení** mapované složky. Každá namapovaná složka má svou vlastní **vlastnost Umístění** nasazení.

### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>Změna umístění nasazení mapované složky

1. V projektu, který jste vytvořili dříve, zvolte namapovanou složku.

2. V **okně Vlastnosti** zvolte tlačítko se třemi tečkami ( ASP.NET Tlačítko se třemi tečkami ![v Mobile Designeru)](../sharepoint/media/mwellipsis.gif "ASP.NET ellipse v Návrháři mobilních aplikací")u vlastnosti **Umístění** nasazení.

3. V dialogovém okně Přidat mapovanou složku **SharePointu** přejděte do složky, do které má mapovaná složka odkazovat.

4. Zvolte uzel a pak zvolte **tlačítko OK.**

## <a name="rename-or-remove-mapped-folders"></a>Přejmenování nebo odebrání mapovaných složek

### <a name="to-rename-or-remove-a-mapped-folder"></a>Přejmenování nebo odebrání mapované složky

1. V projektu, který jste vytvořili dříve, zvolte namapovanou složku.

2. Pokud chcete mapovanou složku přejmenovat, otevřete její místní nabídku, zvolte **Přejmenovat,** zadejte nový název a pak stiskněte klávesu Enter.

     Jako alternativu můžete zvolit mapovanou složku, kterou chcete  přejmenovat, otevřít okno Vlastnosti  a pak nastavit hodnotu vlastnosti Název složky na nový název.

3. Pokud chcete z projektu odebrat namapovanou složku, otevřete její místní nabídku, zvolte Odstranit a potom výběrem tlačítka **OK** v dialogovém okně potvrďte odebrání. 

## <a name="see-also"></a>Viz také

- [Vývoj řešení pro SharePoint](../sharepoint/developing-sharepoint-solutions.md)
