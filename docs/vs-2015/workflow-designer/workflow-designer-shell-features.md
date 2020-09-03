---
title: Funkce prostředí Návrhář postupu provádění | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2c59dc8232713d4126b2c37693a1e241735eb163
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72606604"
---
# <a name="workflow-designer-shell-features"></a>Funkce prostředí návrháře postupu provádění
[!INCLUDE[wfd1](../includes/wfd1-md.md)] se skládá ze tří hlavních oblastí uživatelského rozhraní: plocha návrháře, panel s popisem cesty nad ním a prostředí pod ním. Panel s popisem cesty umístěný v horní části obrazovky slouží k zobrazení seznamu nadřazených prvků aktuální kořenové aktivity. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Postupy: použití navigace s popisem cesty](../workflow-designer/how-to-use-breadcrumb-navigation.md) Plocha návrháře, umístěná uprostřed obrazovky, slouží k vytváření pracovních postupů. Prostředí umístěné v dolní části obrazovky obsahuje řadu tlačítek pro správu aktuálního zobrazení.

## <a name="shell-features"></a>Funkce prostředí
 Prostředí obsahuje tlačítka na pravé straně panelu, který můžete použít k přiblížení nebo oddálení pracovního postupu, přizpůsobení obsahu pracovního postupu velikosti obrazovky a zobrazení nebo skrytí mapy přehledu. Pracovní postup můžete také přiblížit nebo oddálit pomocí klávesových zkratek CTRL + + a CTRL +-.

## <a name="overview-map"></a>Přehledová mapa
 V mapě přehledu se zobrazí malá verze celé aktivity v aktuálním kořenu s popisem cesty, včetně všech jejích potomků a všech jejich rozbalených podřízených objektů. Existuje zobrazení, obdélník s oranžovým ohraničením, který zvýrazní část aktivity aktuálně zobrazenou v editoru. Tažením rámečku kolem mapy přehledu se posune Návrhář pracovního postupu a změní zobrazení editoru.

> [!NOTE]
> [!INCLUDE[wfd2](../includes/wfd2-md.md)]Uživatelské rozhraní je virtualizované. Návrháři aktivit se vykreslují pouze v případě potřeby. Pokud část pracovního postupu nikdy nebyla na návrhové ploše vykreslena, zobrazí se tato část na mapě přehledu jako bílá. Posouváním kolem přehledu mapa zcela nakreslí pracovní postup.

## <a name="copying-or-saving-workflows-as-images"></a>Kopírování a ukládání pracovních postupů jako obrázků
 Pracovní postupy lze kopírovat ve formátu rastrového obrázku nebo uložit ve formátu rastrového obrázku nebo vektoru. Kopírování nebo ukládání obrázku poskytuje způsob, jak exportovat zobrazení celé aktivity v aktuálním kořenu s popisem cesty, včetně všech jejích potomků a všech jejich rozbalených podřízených objektů do jiného programu.

 Chcete-li kopírovat jako obrázek, klikněte pravým tlačítkem myši kdekoli v návrháři a vyberte možnost **Kopírovat jako obrázek**. Pokud chcete uložit jako obrázek, klikněte pravým tlačítkem myši kdekoli v návrháři a vyberte **Uložit jako obrázek**. Pracovní postupy je možné uložit ve formátu JPG, PNG, GIF nebo XPS. Formát je vybrán v dialogovém okně **Uložit jako** v rozevíracím seznamu **Uložit jako typ:** v dolní části okna.

## <a name="fonts-and-colors"></a>Písma a barvy
 Písma použitá v [!INCLUDE[wfd2](../includes/wfd2-md.md)] rámci [!INCLUDE[vs2010](../includes/vs2010-md.md)] jsou ovládána pomocí písma prostředí. [!INCLUDE[wfd2](../includes/wfd2-md.md)]Pokud pro motiv operačního systému používáte barevné schéma s vysokým kontrastem, zobrazené barvy se změní. Je nutné restartovat [!INCLUDE[vs2010](../includes/vs2010-md.md)] po provedení změny nastavení písma nebo barvy, aby se změny projevily [!INCLUDE[wfd2](../includes/wfd2-md.md)] .