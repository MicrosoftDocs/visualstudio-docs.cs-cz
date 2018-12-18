---
title: 'Postupy: získání přehledu o sadě schémat pomocí zobrazení grafu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3722af4aef2f56d6da1c2a79840c05edd2a87b65
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181360"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Postupy: získání přehledu o sadě schémat pomocí zobrazení grafu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Toto téma popisuje způsob použití [zobrazení grafu](../xml-tools/graph-view.md) zobrazíte souhrnný přehled uzly v sadě schémat a vztahy mezi uzly.  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Vytvořte nový soubor XSD a zobrazte kořenový element v zobrazení modelu obsahu  
  
1.  Vytvořte nový soubor schématu XML a uložte soubor jako Relationships.xsd.  
  
2.  Klikněte na tlačítko **pomocí editoru XML k zobrazení a úpravě základního souboru schématu XML** odkaz na zobrazení spuštění.  
  
3.  Zkopírujte ukázkový kód XML schéma z [ukázky XML schématu: relace](../xml-tools/sample-xsd-file-relationships.md) a vložte ji nahradit kód, který byl přidán do nového souboru XSD ve výchozím nastavení.  
  
4.  Klikněte pravým tlačítkem na libovolné místo v editoru XML a vyberte **Návrhář zobrazení**.  
  
5.  Zobrazení grafu vyberte na panelu nástrojů XSD.  
  
6.  Vyberte **schéma nastaveno** uzlu Průzkumníka schémat XML a přetáhněte uzel návrhu suface zobrazení grafu. Měli byste vidět všechny globální uzly a šipky spojující uzly, které mají relace.  
  
     ![Zobrazení grafu](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")  
  
7.  Klikněte na libovolný uzel na návrhové ploše a podívejte se na panelu s popisem cesty chcete zobrazit, kde se nachází na vybraný uzel v sadě schémat.  
  
8.  Rick kliknutím na libovolný uzel elementu na desing ploše a vyberte možnost **generovat ukázkové XML** zobrazíte instance dokumentu XML.



