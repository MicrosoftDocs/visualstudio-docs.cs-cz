---
title: Funkce prostředí návrháře postupu provádění
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5d881a6c6e14983fd8537d8e78066ef9479b9633
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757200"
---
# <a name="workflow-designer-shell-features"></a>Funkce prostředí návrháře postupu provádění

Návrhář postupu provádění se skládá ze tří hlavních oblastí uživatelského rozhraní: plochu návrháře, navigačního panelu nad ním a pod ním prostředí. Navigačního panelu, umístěný v horní části obrazovky se používá k zobrazení seznamu nadřazených aktuální kořenové aktivity. Další informace najdete v tématu [postupy: použití navigace](../workflow-designer/how-to-use-breadcrumb-navigation.md). Plochu návrháře umístěný v centru obrazovky se používá k vytváření pracovních postupů. Prostředí, umístěný v dolní části obrazovky, obsahuje řadu tlačítek pro Správa aktuálního zobrazení.

## <a name="shell-features"></a>Funkce prostředí
 Prostředí má tlačítka na pravé straně panelu můžete zvětšit nebo zmenšit pracovní postup, podle obsahu pracovního postupu na velikost obrazovky a zobrazit nebo skrýt mapu přehledu. Také můžete zvětšit nebo zmenšit pracovní postup pomocí klávesové zkratky CTRL ++ a CTRL +-.

## <a name="overview-map"></a>Přehled mapy
 Přehled mapa zobrazuje malé verzi celý aktivity v aktuální kořenové s popisem cesty, včetně všech jejích podřízených a všemi podřízenými rozšířené. Je zobrazení, obdélníku s oranžové ohraničení, který označuje části aktivity zobrazené v editoru. Přetahování rámeček kolem mapu přehledu posune návrháře pracovních postupů a změní zobrazení editoru.

> [!NOTE]
> Návrhář postupu provádění uživatelské rozhraní je virtualizované. Návrháře aktivit jsou vykreslovány pouze v případě potřeby. Část pracovní postup nebylo nikdy řádně na plochu návrháře, část se zobrazí jako bílé na mapu přehledu. Posouvání kolem mapu přehledu úplně nevykresluje pracovního postupu.

## <a name="copying-or-saving-workflows-as-images"></a>Kopírování nebo uložení pracovních jako obrázky
 Pracovní postupy můžete zkopírovat ve formátu rastrového obrázku nebo uložit ve formátu rastrového obrázku nebo vektoru. Kopírování nebo uložení obrázku poskytuje způsob, jak exportovat zobrazení celý aktivity v aktuální kořenové s popisem cesty, včetně všech jejích podřízených a všemi podřízenými rozšířené na jiném programu.

 Pokud chcete zkopírovat bitovou kopii, klikněte pravým tlačítkem někde v návrháři a vyberte **kopie jako obrázek**. Pokud chcete uložit jako bitovou kopii, klikněte pravým tlačítkem na libovolné místo v návrháři a vyberte **uložit jako obrázek**. Pracovní postupy lze uložit ve formátu JPG, GIF, PNG nebo XPS. Formát je vybrané na **uložit jako** dialogovém okně **uložit jako typ:** rozevírací seznam v dolní části okna.

## <a name="fonts-and-colors"></a>Písma a barev

Písma použitá v Návrháři pracovních postupů v prostředí Visual Studio jsou řízeny písmo prostředí. Pokud používáte schéma s vysokým kontrastem barvu motivu operačního systému změnit barev zobrazí v Návrháři pracovních postupů. Po provedení změny nastavení písma a barev, než změny se projeví v Návrháři pracovních postupů, musíte restartovat Visual Studio.