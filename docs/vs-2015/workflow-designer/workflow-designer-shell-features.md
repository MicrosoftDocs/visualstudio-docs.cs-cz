---
title: Funkce prostředí návrháře postupu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 0f75d545055a4657ed4cefdbafe211ea2f34680f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49275298"
---
# <a name="workflow-designer-shell-features"></a>Funkce prostředí návrháře postupu provádění
[!INCLUDE[wfd1](../includes/wfd1-md.md)] se skládá ze tří hlavních oblastech uživatelského rozhraní: na plochu návrháře, panelu navigace s popisem cesty nad ním a pod ním prostředí. Na panelu navigace s popisem cesty umístěný v horní části obrazovky, slouží k zobrazení seznamu nadřazených členů aktuální kořenovou aktivitu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Postupy: použití navigace s popisem cesty](../workflow-designer/how-to-use-breadcrumb-navigation.md). Na plochu návrháře umístěn ve středu obrazovky, slouží k vytváření pracovních postupů. Prostředí, které jsou umístěné v dolní části obrazovky obsahuje řadu tlačítek pro Správa aktuálního zobrazení.  
  
## <a name="shell-features"></a>Prostředí funkce  
 Prostředí má tlačítka na pravé straně panelu, který vám umožní zvětšit nebo zmenšit pracovního postupu, přizpůsobit obsah pracovního postupu na velikost obrazovky a zobrazit nebo skrýt přehledovou mapu. Můžete také přiblížit nebo oddálit pracovního postupu pomocí klávesové zkratky CTRL ++ a CTRL +-.  
  
## <a name="overview-map"></a>Přehledovou mapu  
 Přehledovou mapu jako malé verze celá aktivita zobrazí aktuální kořenové navigace s popisem cesty, včetně všech jeho podřízených prvků a všemi podřízenými rozšířené. Zde je zobrazení, obdélník se oranžové ohraničení, která zvýrazňuje část aktivity aktuálně zobrazený v editoru. Přetahování obdélník kolem přehledovou mapu posune návrháře pracovních postupů a změní zobrazení editoru.  
  
> [!NOTE]
>  [!INCLUDE[wfd2](../includes/wfd2-md.md)] Virtualizované uživatelské rozhraní. Návrháři aktivit jsou generovány pouze v případě potřeby. Část pracovního postupu byl nakreslen nikdy na návrhové ploše, část se zobrazí jako bílá na přehledovou mapu. Posouvání kolem přehledovou mapu zcela kreslení pracovního postupu.  
  
## <a name="copying-or-saving-workflows-as-images"></a>Kopírování nebo ukládání pracovních postupů jako obrázky  
 Pracovní postupy dá zkopírovali v formát rastrového obrázku nebo uložit ve formátu rastrový obrázek nebo vektoru. Kopírování nebo ukládání obrazu poskytuje způsob, jak exportovat zobrazení celého aktivity aktuální kořenové navigace s popisem cesty, včetně všech jeho podřízených prvků a všemi podřízenými rozšířené na jiném programu.  
  
 Pokud chcete zkopírovat jako obrázek, klikněte pravým tlačítkem kamkoli v návrháři a vyberte **zkopírovat jako obrázek**. Uložit jako obrázek, klikněte pravým tlačítkem na libovolné místo v návrháři a vyberte **uložit jako obrázek**. Pracovní postupy je ukládat ve formátu JPG, GIF, PNG nebo XPS. Formát je vybrán na **uložit jako** dialogovém **uložit jako typ:** rozevírací seznam v dolní části okna.  
  
## <a name="fonts-and-colors"></a>Písma a barvy  
 Písma použitého v [!INCLUDE[wfd2](../includes/wfd2-md.md)] uvnitř [!INCLUDE[vs2010](../includes/vs2010-md.md)] jsou řízeny písmo prostředí. Barvy zobrazené v [!INCLUDE[wfd2](../includes/wfd2-md.md)] změnit, pokud používáte kontrastní barevné schéma pro motivu operačního systému. Je nutné restartovat [!INCLUDE[vs2010](../includes/vs2010-md.md)] po provedení změny nastavení písma a barvy, než se změny projeví v [!INCLUDE[wfd2](../includes/wfd2-md.md)].