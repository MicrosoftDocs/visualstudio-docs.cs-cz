---
title: 'Postupy: prozkoumání modelu obsahu uzlů pomocí zobrazení modelu obsahu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ca6c86772cc3ad27b537052961afea50fad7b876
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245944"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Postupy: prozkoumání modelu obsahu uzlů pomocí zobrazení modelu obsahu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Toto téma popisuje, jak prozkoumat uzly pomocí [zobrazení modelu obsahu](../xml-tools/content-model-view.md).  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Vytvořte nový soubor XSD a zobrazte kořenový element v zobrazení modelu obsahu  
  
1.  Vytvořte nový soubor schématu XML.  
  
2.  Klikněte na tlačítko **pomocí editoru XML k zobrazení a úpravě základního souboru schématu XML** na zobrazení spuštění.  
  
3.  Zkopírujte ukázkový kód XML schéma z [ukázky XML schématu: nákupní pořadí schématu](../xml-tools/sample-xsd-file-purchase-order-schema.md) a vložte ji nahradit kód, který byl přidán do nového souboru XSD ve výchozím nastavení.  
  
4.  Vyberte `purchaseOrder` element ve schématu Explorer kliknutím pravým tlačítkem myši `purchaseOrder` element v editoru XML a vyberete **zobrazit v Průzkumníkovi XML**.  
  
5.  Klikněte pravým tlačítkem myši `purchaseOrder` v Průzkumníku XML a vyberte **zobrazit v zobrazení modelu obsahu**.  
  
     Zobrazení modelu obsahu se zobrazí `purchaseOrder` prvek na jeho návrhovou plochu.  
  
6.  Rozbalte `shipTo`, `billTo`, a `items` uzlů poklepáním na každém uzlu nebo kliknutím na dvojitou šipku vpravo od každého uzlu.  
  
     Uzly `purchaseOrder` prvek nyní rozbaleny a zobrazí se model obsahu prvku.  
  
7.  Klikněte na libovolný uzel v rámci `purchaseOrder` elementu a podívejte se na panelu s popisem cesty chcete zobrazit, kde v sadě schémat vybraný uzel se nachází.  
  
8.  Klikněte na tlačítko **zobrazit dokumentaci** tlačítko na panelu nástrojů XSD, chcete-li přepnout jejich. Klikněte pravým tlačítkem na návrhové ploše, chcete-li přepnout v dokumentaci.  
  
9. Rick kliknutím `purchaseOrder` uzel a vyberte možnost **generovat ukázkové XML** zobrazíte instance dokumentu XML.



